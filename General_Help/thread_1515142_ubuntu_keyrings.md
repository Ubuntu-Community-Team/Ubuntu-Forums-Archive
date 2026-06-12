---
title: "ubuntu keyrings"
date: 2010-06-21
forum: General Help
---

### Post by ajtwin on 2010-06-21
after i installed some linux mint packages, i get the following error.


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5

its not related to the mint packages because i installed the keyring for that and since the error i have unchecked the linux mint repo.

i have tried reinstalling the ubuntu-keyring package with no luck.

any ideas?

---

### Post by lindsay7 on 2010-06-22
Here are the commands to type into the terminal and the detail on this.


gpg --keyserver keyserver.ubuntu.com --recv keynumber

gpg --export --armor keynumber | sudo apt-key add -
then run

sudo apt-get update

 Re: No_pubkey
That is asking you for the public key to that repository. In linux you will see lots of people sign programs,emails, etc with a public key. Some repositories have a public key which you need to download to access. There are a few pages on wikipedia about it [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
All you need to know is the process to use when you see that. This is the template
Code:

    gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

When you get an error message, replace the word "KEY" with the numbers in the eror message. For your error you would enter this command
Code:

 gpg --keyserver subkeys.pgp.net --recv F120156012B83718

After you press enter and it sends the command, you would enter the second line
Code:

 gpg --export --armor F120156012B83718 | sudo apt-key add -

After that, the key will be added to a list and the error will not appear.

---

### Post by ajtwin on 2010-06-22
well, it turns out the missing keyring is from installing BURG, not the linux mint packages. and i followed the instructions, but it didn't appear to work. i just unchecked the burg repo so i don't have to worry about the error anymore. thanks. ;)

---

