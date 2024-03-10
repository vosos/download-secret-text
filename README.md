# Download Secret Text

The Download Secret Text  GitHub Action is designed for developers who need a robust solution for encrypting sensitive information. Whether you're taking over a repository without documented secrets or simply securing your project's data, this action uses GPG encryption to ensure your secrets remain safe. Alongside tools like the [Mystery Token Explorer](https://github.com/marketplace/actions/mystery-token-explorer), it forms a crucial part of your security and forensics toolkit, allowing for the encryption of any text, including repository secrets, into a GPG-encrypted format.

## Highlights
- **GPG Encryption:** Securely encrypts provided text using a GPG public key.
- **Versatile Use:** Ideal for encrypting repository secrets or any sensitive information.
- **Downloadable** encrypted file. (look for it in the `summary`)

![downloadable encrypted file](/screenshots/download-artifact.png)

## Inputs
- `gpg_public_key`: Your GPG public key.
- `plain_text`: Text to encrypt.

## Generating a GPG key pair

GitHub's own [***T U T O R I A L***](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key#generating-a-gpg-key) is a great resource to help you setup a GPG key pair. The `public` part of that key is what you will have to provide to this action. The `private` part of the key and your personal `secret` is what makes the decryption possible. 

## Examples
```yaml
steps:
- uses: vosos/download-secret-text@v1
  with:
    gpg_public_key: ${{ secrets.GPG_PUBLIC_KEY }}
    plain_text: 'Sensitive information'
```
---
```yaml
    steps:
    - uses: vosos/download-secret-text@v1
    with:
        gpg_public_key: ${{ vars.GPG_PUBLIC_KEY }}
      # gpg_public_key: ${{ secrets.GPG_PUBLIC_KEY }}
        plain_text: |
            SOME_API_KEY=${{ secrets.SOME_API_KEY }}
            FYE_SECRET_ONE=${{ secrets.FYE_SECRET_ONE }}
            FYE_SECRET_TWO=${{ secrets.FYE_SECRET_TWO }}
            SOME_TOKEN=${{ secrets.SOME_TOKEN }}
```
---
```yaml
    steps:
    - uses: vosos/download-secret-text@v1
    with:
        gpg_public_key: |
            -----BEGIN PGP PUBLIC KEY BLOCK-----

            mQINBGXrnl0BAACsF..AhHGSZaBtlAaa9KN1
            4PXZFkMWrIhoMxNPP..NLnyGOvHGwSytiVgP
            GMa11QufbaIi4XW9b..M6+NPX6usdwCkjIK3
            ....................................
            x1VprAAG8iG9a4Ctb..WAsK1QLW6OCLcPBiZ
            +2xoIwFCbMVoBiHBT..6mGYhvQT84hmzhjk2
            Cp2GbkVVvF6bGvt3k..iBnL4ZMYXAFz0FZVb
            JpdJsr+W2MWqaPPod..yXpAmqOGdCHFnTzj
            =cP3n
            -----END PGP PUBLIC KEY BLOCK-----
        plain_text: |
            SOME_API_KEY=${{ secrets.SOME_API_KEY }}
            FYE_SECRET_ONE=${{ secrets.FYE_SECRET_ONE }}
            FYE_SECRET_TWO=${{ secrets.FYE_SECRET_TWO }}
            SOME_TOKEN=${{ secrets.SOME_TOKEN }}
```

This action not only encrypts plain text but also securely handles the secrets of any repository, ensuring a smooth and secure transition for project handovers or audits.

## Contributing
Enhancements or documentation improvements are welcomed, making use of the `issues` tab.
