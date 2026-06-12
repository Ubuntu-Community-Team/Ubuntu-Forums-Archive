---
title: "Question about encrypting files..."
date: 2012-06-02
forum: General Help
---

### Post by FitzLT on 2012-06-02
Good afternoon everyone.  I have have been using openssl to encrypt my compressed files.  I recently decided to try GPG and like how it's as easy to use as openssl.  I did, however, have one problem with it.

When encrypting files with a passphrase in openssl, you have to know the exact cipher used(along with the passphrase) to decrypt the file.  Openssl **will not** give you any hints as to what cipher was used.

GnuPG, however, will not only tell you what cipher was used(regardless of whether you entered the correct passphrase or not)--but will also decrypt the file if the correct passphrase is entered **even if a cipher algorithm was never specified**!

Here are my questions...:
1)  Is there a way to prevent GPG from announcing what cipher was used to encrypt a file **before** decryption?

2)  Is there a way to require users to specify the cipher needed to decrypt a file with GPG?

3)  If the two questions above are not possible, are there other alternatives?

I ask the third question because I ran into a problem where I had to temporarily use a Windows computer and there were no binary packages for openssl available for Windows.  Without access to openssl, I couldn't access my encrypted files.

I really love openssl, but I need to use a program that is accessible from virtually every major operating system.  I love GPG, but do not like(what appears to me) the default security methods.

Thank you all in advance.

---

### Post by jenic on 2012-06-03
As far as I know there is no mention of such an option. Is that really necessary though? Just because they know your file is RSA 4096 encrypted (or if symmetric, AES256) doesn't mean they are going to break it.

It's kinda like this:

Ha! I know your using AES-256-CBC and in 4 billion years I'll be able to steal your cat pictures!

---

### Post by FitzLT on 2012-06-04
> **jenic said:**
> As far as I know there is no mention of such an option. Is that really necessary though? Just because they know your file is RSA 4096 encrypted (or if symmetric, AES256) doesn't mean they are going to break it.

It's kinda like this:

Ha! I know your using AES-256-CBC and in 4 billion years I'll be able to steal your cat pictures!

LOL.  I take it then that it is a non-issue...

That was all I needed to know.  If knowing the cipher doesn't really matter, then I won't worry about it.  I'm just overly cautious since I do have some sensitive data in one of my files(kept on-line in case of possible future issues).

Thank you very much for your reply!

---

### Post by jenic on 2012-06-04
> **FitzLT said:**
> LOL.  I take it then that it is a non-issue...

That was all I needed to know.  If knowing the cipher doesn't really matter, then I won't worry about it.  I'm just overly cautious since I do have some sensitive data in one of my files(kept on-line in case of possible future issues).

Thank you very much for your reply!

You are most welcome!

Remember though, the encryption is only as strong as the passphrase that is directly (in the case of symmetric) or indirectly (in the case of your private key) protecting your data. Make your passphrase long, unique, with numbers, punctuation, and non-dictionary words if you can help it. Preferably use RSA-256 (in the case of symmetric) or RSA-4096 (in the case of public key.) I generally mix made up words with real ones, punctuating them in funny but memorable ways.

Keeping the data online is risky but sometimes unavoidable. I am a very serious tinfoil hatter so naturally I shudder at something like that but I recognize not everyone is as crazy as I am.

Good luck! :)

---

