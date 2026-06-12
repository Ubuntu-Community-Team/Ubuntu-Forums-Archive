---
title: "Question about file encryption with GPG"
date: 2010-09-03
forum: General Help
---

### Post by JohnElway on 2010-09-03
I've just started using the GNU Privacy Guard for encrypting some important files. However, because there are many files I need to protect, I put together a script to encrypt each file. Everything works fine, except that I still have to manually enter in my passphrase for each encrypted file. Is there any way that I can include my passphrase in the gpg command so that I don't have to enter it in numerous times?

---

### Post by Bachstelze on 2010-09-03
**Don't** do that! You don't want your passphrase stored in clear in your shell history. ;)

You can use gpg-agent, it should be as simple as

```
sudo apt-get install gnupg-agent
```

Then log out and back in.

---

### Post by JohnElway on 2010-09-03
What is gpg-agent? I have the GNU Privacy Assistant installed. Would this do what gpg-agent does?

---

### Post by Bachstelze on 2010-09-03
I don't know what "GNU Privacy Assistant" is. gpg-agent rmeembers your passphrase in a secure way, so you don't have to do stupid things like pass it on the command line, or create a key without a passphrase. ;)

---

### Post by JohnElway on 2010-09-03
I was just snooping around Synaptic checking out the different gpg packages available and saw that I already have gpg-agent installed. It doesn't seem to remember the passphrases by default. Am I supposed to configure anything?

---

### Post by hakermania on 2010-09-03
Your bash history is saved in plain text. So, don't specify any password in there because are easily viewable

---

### Post by Bachstelze on 2010-09-03
> **JohnElway said:**
> I was just snooping around Synaptic checking out the different gpg packages available and saw that I already have gpg-agent installed. It doesn't seem to remember the passphrases by default. Am I supposed to configure anything?

Maybe you don't have a pinentry program installed, I don't remember if there is one installed automatically when you install gpg-agent. Do you get any warnings before you enter your passphrase?

---

### Post by surfer on 2010-09-03
i you need to encrypt multiple files, you could also set up an eCryptfs or (somewhat simpler) an encfs directory.

you type in the password once to decrypt the directory (and its subfolders) and you can unmount it again (in userspace, you don't have to be root) so only the encrypted variant is left.

it's just passphrase security, your gpg keys will not be used.

---

### Post by JohnElway on 2010-09-03
> **Bachstelze said:**
> Maybe you don't have a pinentry program installed, I don't remember if there is one installed automatically when you install gpg-agent. Do you get any warnings before you enter your passphrase?

When I try to encrypt I get multiple windows asking for my passphrase and the title of each of these windows is 'pinentry'. Before each window pops up the following is printed in the terminal:

```
gpg: CAST5 encrypted data
```After I enter my passphrase this gets printed:

```
gpg: encrypted with 1 passphrase
gpg: WARNING: message was not integrity protected
```Does this mean anything?

EDIT: I also checked to make sure that gpg-agent is running, using 'pidof gpg-agent', and it appears to be running.

EDIT2: Just found this:

[http://www.debian-administration.org/article/Using_gnupg-agent_to_securely_retain_keys](http://www.debian-administration.org/article/Using_gnupg-agent_to_securely_retain_keys)

I know I have gpg-agent installed and running. I added 'eval $(gpg-agent)' to the beginning of both of my scripts but nothing has changed. I checked the ~/.gnupg/gpg.conf file and it already has the 'use-agent' line uncommented. I also have a pinentry program installed.

Any ideas what could be going wrong? Should I try a different gpg passphrase program?

---

