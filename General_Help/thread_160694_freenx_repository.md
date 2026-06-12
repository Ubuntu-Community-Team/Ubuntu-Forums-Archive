---
title: "freenx repository"
date: 2006-04-15
forum: General Help
---

### Post by rvergara on 2006-04-15
I am trying to find an ubuntu repository that contains freenx at no avail, I have tried:

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx
deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) breezy-seveas

In all of them I get "folder or file does not exist"

Are all the seveas repositories down or moved to a different url?

Thanks for any help on this

Regards

Ramiro

---

### Post by Ramses de Norre on 2006-04-15
These seem to work: ```

deb http://free.linux.hp.com/~brett/seveas/freenx/ breezy-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx/ breezy-seveas freenx
```

---

### Post by rvergara on 2006-04-15
Ramses,

That one is one of the repositories that I reported as not working. Have you tried it lately, is it working for you today?

Maybe I am doing something wrong when adding the repository in sources.list

Regards

Ramiro

---

### Post by Ramses de Norre on 2006-04-15
It worked when I posted it and it works now..
You just added the lines at the bottom of the file with nothing else on the same lines? You did a sudo apt-get update?

---

### Post by rvergara on 2006-04-15
I was actually using synaptic.

I have added a couple of repositories for different software (other than freenx) without a problem. 

When I try sudo apt-get from the terminal, it prompts with a GPG error:

GPG error: [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas Release:The following signatures couldn't be verified because the public key is not available: NO_PUBKEY XXXXXXXXXXX


What is the problem?

Ramiro

---

### Post by rvergara on 2006-04-15
never mind. I found the solution.

In the seveas web site there was the following note:

Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is 1135D466. You can enter this key into the APT trusted keys database with the following commands:
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -

I thought this was optional. Apparently it is not.

Thanks anyway.

Ramiro

---

### Post by Ramses de Norre on 2006-04-15
```
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -
```
too late ;)

---

