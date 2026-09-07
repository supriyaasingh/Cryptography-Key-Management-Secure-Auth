# Cryptography, Key Management & Secure Authentication

> **Educational Security Project**
> This repository demonstrates secure cryptographic and authentication practices using Python and established cryptographic libraries. All keys, passwords, and secrets used in demonstrations are synthetic and for educational purposes only.

---

## 📌 Project Overview

This project demonstrates the implementation and secure use of common cryptographic mechanisms and authentication controls in Python.

The project focuses on:

* AES-256-GCM authenticated encryption
* RSA-2048 key-pair generation
* RSA-PSS digital signatures
* HMAC-SHA-256
* bcrypt password hashing
* Secure key management
* Key rotation
* Secret storage
* Secure authentication practices

The project emphasizes **using established cryptographic libraries correctly** rather than implementing cryptographic algorithms from scratch.

---

## 🎯 Objectives

The main objectives are to:

1. Implement AES-256-GCM encryption and decryption.
2. Generate RSA-2048 public/private key pairs.
3. Create and verify RSA digital signatures.
4. Implement HMAC-SHA-256 message authentication.
5. Securely hash passwords using bcrypt.
6. Demonstrate secure cryptographic key generation.
7. Demonstrate key versioning and rotation.
8. Document secure secret and key storage practices.
9. Create automated security tests.
10. Demonstrate secure authentication concepts.

---

## 🛠️ Technology Stack

| Technology     | Purpose                                  |
| -------------- | ---------------------------------------- |
| Python 3       | Primary programming language             |
| `cryptography` | AES-GCM and RSA cryptographic operations |
| `bcrypt`       | Secure password hashing                  |
| `pytest`       | Automated testing                        |
| Git/GitHub     | Version control and project hosting      |

---

# 🔐 Cryptographic Components

## 1. AES-256-GCM

AES-256-GCM is used for authenticated symmetric encryption.

The implementation provides:

* 256-bit encryption keys
* Cryptographically secure random nonces
* Authenticated encryption
* Authentication of additional data (AAD)
* Tamper detection
* Secure decryption

Conceptually:

```text
Plaintext
    |
    v
AES-256-GCM + Random Nonce
    |
    v
Ciphertext + Authentication Tag
```

The project demonstrates why a **fresh nonce must be generated for every encryption operation when using the same key**.

Implementation:

```text
src/aes_gcm.py
```

Example:

```text
examples/aes_example.py
```

Tests:

```text
tests/test_aes_gcm.py
```

---

# 🔑 2. RSA-2048

The project generates RSA-2048 public/private key pairs.

The RSA implementation is used for digital signatures rather than bulk data encryption.

Conceptually:

```text
             RSA Key Pair

       ┌────────────────────┐
       │                    │
       ▼                    ▼
  Private Key           Public Key
       │                    │
       ▼                    ▼
     Sign                Verify
```

The implementation uses:

**RSA-PSS with SHA-256**

This demonstrates:

* Key-pair generation
* Digital signatures
* Signature verification
* Message integrity
* Authentication of the signer

Implementation:

```text
src/rsa_signatures.py
```

Example:

```text
examples/rsa_example.py
```

Tests:

```text
tests/test_rsa.py
```

---

# 🔏 3. HMAC-SHA-256

HMAC provides message authentication and integrity using a shared secret.

The project uses:

**HMAC-SHA-256**

Conceptually:

```text
Message + Secret Key
        |
        v
     HMAC-SHA-256
        |
        v
 Authentication Tag
```

The implementation demonstrates:

* HMAC generation
* HMAC verification
* Tampered message detection
* Incorrect secret detection
* Secure comparison

Implementation:

```text
src/hmac_utils.py
```

Example:

```text
examples/hmac_example.py
```

Tests:

```text
tests/test_hmac.py
```

---

# 🔒 4. bcrypt Password Hashing

Passwords are protected using **bcrypt**.

Passwords are never stored as plaintext.

Conceptually:

```text
User Password
      |
      v
   bcrypt
      |
      v
Salted Password Hash
      |
      v
Stored Password Hash
```

The implementation demonstrates:

* Password hashing
* Automatic salting
* Work factor
* Password verification
* Incorrect password rejection

Implementation:

```text
src/password_hashing.py
```

Example:

```text
examples/password_example.py
```

Tests:

```text
tests/test_password_hashing.py
```

---

# 🔐 Key Management

The project demonstrates secure key-management principles including:

* Cryptographically secure key generation
* Key identifiers
* Key versioning
* Key rotation
* Key expiration concepts
* Key separation
* Secret storage
* Key revocation
* Secure deletion

Implementation:

```text
src/key_management.py
```

Documentation:

```text
docs/key-management.md
```

---

# 🔄 Key Rotation

Key rotation is demonstrated using versioned keys.

Example lifecycle:

```text
Key Version 1
      |
      v
New Key Generated
      |
      v
Key Version 2
      |
      v
New Data → Version 2
      |
      v
Version 1 Retired
```

Key rotation helps reduce the impact of long-term key exposure and supports controlled cryptographic lifecycle management.

---

# 🔑 Secret Storage

The project documents secure approaches to storing cryptographic secrets.

Recommended approaches include:

### Development

* Environment variables
* Local secret stores
* Protected development configuration

### Production

* Dedicated secret-management systems
* Cloud Key Management Services
* Hardware Security Modules where appropriate
* Strong access controls
* Audit logging

A `.env` file should **not** be considered a complete production secret-management solution.

Never commit secrets or private keys to GitHub.

---

# 🛡️ Secure Authentication

The project contains an educational authentication demonstration using:

* bcrypt password hashing
* Password verification
* Secure secret handling
* Authentication concepts

Demo:

```text
demo/secure_auth_demo.py
```

The demo uses synthetic credentials only.

Example:

```text
Username: demo_user
Password: DemoPassword123!
```

These credentials are for demonstration purposes and must never be reused for real accounts.

---

# 🧪 Security Testing

Automated tests are provided using `pytest`.

The tests verify important security properties.

### AES-256-GCM

* Encryption/decryption
* Wrong key rejection
* Ciphertext tampering detection
* Nonce modification detection
* AAD modification detection

### RSA

* Key generation
* Signature generation
* Valid signature verification
* Modified message rejection
* Modified signature rejection
* Wrong key rejection

### HMAC

* Valid HMAC verification
* Modified message rejection
* Modified HMAC rejection
* Wrong secret rejection

### bcrypt

* Password hashing
* Correct password verification
* Incorrect password rejection
* Salt behavior

---

# 📁 Repository Structure

```text
cryptography-secure-auth/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── src/
│   ├── __init__.py
│   ├── aes_gcm.py
│   ├── rsa_signatures.py
│   ├── hmac_utils.py
│   ├── password_hashing.py
│   └── key_management.py
│
├── examples/
│   ├── aes_example.py
│   ├── rsa_example.py
│   ├── hmac_example.py
│   └── password_example.py
│
├── tests/
│   ├── test_aes_gcm.py
│   ├── test_rsa.py
│   ├── test_hmac.py
│   ├── test_password_hashing.py
│   └── test_key_management.py
│
├── demo/
│   └── secure_auth_demo.py
│
└── docs/
    ├── cryptography-overview.md
    ├── key-management.md
    ├── secure-authentication.md
    ├── threat-model.md
    └── security-best-practices.md
```

---

# 🚀 Installation

## 1. Clone the repository

```bash
git clone <your-repository-url>
cd cryptography-secure-auth
```

Replace `<your-repository-url>` with the actual GitHub repository URL.

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

### Linux/macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Examples

## AES Example

```bash
python examples/aes_example.py
```

Demonstrates:

* Key generation
* Encryption
* Decryption
* Authentication/tamper detection

---

## RSA Example

```bash
python examples/rsa_example.py
```

Demonstrates:

* RSA-2048 key generation
* Digital signature
* Signature verification
* Modified message rejection

---

## HMAC Example

```bash
python examples/hmac_example.py
```

Demonstrates:

* HMAC generation
* HMAC verification
* Tamper detection

---

## Password Example

```bash
python examples/password_example.py
```

Demonstrates:

* bcrypt password hashing
* Password verification
* Incorrect password rejection

---

# 🧪 Running Tests

Run the complete test suite:

```bash
pytest
```

For more detailed output:

```bash
pytest -v
```

The test suite should verify both normal functionality and security failure cases.

---

# ⚠️ Security Considerations

This project follows several important security principles.

### Never implement cryptography from scratch

Use established and reviewed cryptographic libraries.

### Use secure random generation

Cryptographic keys and nonces must be generated using a cryptographically secure random source.

### Never reuse AES-GCM nonces

Nonce reuse with the same AES-GCM key can seriously compromise security.

### Protect private keys

Private keys must remain confidential.

### Never store plaintext passwords

Passwords should be protected using an appropriate password-hashing algorithm such as bcrypt.

### Never hard-code secrets

Secrets should be supplied through an appropriate secret-management mechanism.

### Do not log secrets

Application logs should never expose:

* Passwords
* Private keys
* API keys
* Encryption keys
* Authentication tokens

---

# 📚 Documentation

Additional documentation is available in:

```text
docs/
```

### Cryptography Overview

`docs/cryptography-overview.md`

Explains the cryptographic mechanisms used in the project.

### Key Management

`docs/key-management.md`

Explains:

* Key storage
* Key lifecycle
* Key rotation
* Key revocation
* Secret management

### Secure Authentication

`docs/secure-authentication.md`

Explains secure password and authentication practices.

### Threat Model

`docs/threat-model.md`

Documents threats involving:

* Password compromise
* Key theft
* Secret exposure
* Weak randomness
* Nonce reuse
* Tampering
* Authentication failures

### Security Best Practices

`docs/security-best-practices.md`

Provides defensive security recommendations.

---

# 🔄 Cryptographic Mechanism Comparison

| Mechanism    | Primary Purpose        | Key Type         | Confidentiality | Integrity / Authentication |
| ------------ | ---------------------- | ---------------- | --------------- | -------------------------- |
| AES-256-GCM  | Encryption             | Symmetric        | ✅               | ✅                          |
| RSA-PSS      | Digital signatures     | Asymmetric       | ❌               | ✅                          |
| HMAC-SHA-256 | Message authentication | Shared secret    | ❌               | ✅                          |
| bcrypt       | Password storage       | Password hashing | ❌               | Password verification      |

---

# 🔒 Git Security

The repository uses `.gitignore` to prevent accidental commits of sensitive material.

Examples of excluded files include:

```text
.env
.venv/
*.pem
*.key
*.p12
*.pfx
generated_keys/
secrets/
__pycache__/
```

Before pushing the repository to GitHub, verify that no private keys, passwords, tokens, or other secrets are present.

---

# ⚠️ Limitations

This is an **educational cryptography and secure-authentication project**.

It is not intended to replace:

* Enterprise Key Management Systems
* Hardware Security Modules
* Cloud KMS
* Production identity platforms
* Professional cryptographic review
* Security architecture review

Correct cryptographic security depends not only on the algorithm but also on:

* Correct implementation
* Key management
* Secret storage
* Application architecture
* Access controls
* Operational security

---

# 🎓 Learning Outcomes

After completing this project, the student should understand:

* Symmetric encryption
* Authenticated encryption
* AES-GCM
* Nonce/IV management
* Asymmetric cryptography
* RSA key pairs
* Digital signatures
* HMAC
* Password hashing
* Salting
* Work factors
* Key management
* Key rotation
* Secret storage
* Secure authentication
* Cryptographic testing

---

# ✅ Project Completion Checklist

## AES-256-GCM

* [ ] 256-bit key generation
* [ ] Random nonce generation
* [ ] Encryption
* [ ] Decryption
* [ ] Authentication/tag verification
* [ ] Tamper detection
* [ ] AAD support

## RSA-2048

* [ ] Key-pair generation
* [ ] Public/private key handling
* [ ] RSA-PSS signature generation
* [ ] Signature verification
* [ ] Tampered message detection

## HMAC

* [ ] HMAC-SHA-256
* [ ] Secure secret generation
* [ ] HMAC verification
* [ ] Tamper detection
* [ ] Secure comparison

## Password Security

* [ ] bcrypt
* [ ] Automatic salting
* [ ] Work factor
* [ ] Password verification
* [ ] No plaintext password storage

## Key Management

* [ ] Secure key generation
* [ ] Key versioning
* [ ] Key rotation
* [ ] Key lifecycle documentation
* [ ] Secret storage documentation

## Testing

* [ ] Unit tests
* [ ] Security failure tests
* [ ] All tests passing

## Documentation

* [ ] Cryptography overview
* [ ] Key management
* [ ] Secure authentication
* [ ] Threat model
* [ ] Security best practices
* [ ] README

---

# ⚖️ Ethical & Security Statement

This project is intended for **educational cybersecurity, secure software development, and defensive security research**.

All keys, passwords, credentials, and data used in demonstrations are synthetic.

Never use demonstration secrets in production.

Never commit private keys, passwords, API keys, or other sensitive information to a public repository.

---

## Author

**Name:** [Your Name]
**Project:** Cryptography, Key Management & Secure Authentication
**Technology:** Python 3
**Purpose:** Cybersecurity Education / Security Engineering
