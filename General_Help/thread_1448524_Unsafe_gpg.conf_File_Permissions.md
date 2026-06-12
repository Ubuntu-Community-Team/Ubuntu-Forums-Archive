---
title: "Unsafe gpg.conf File Permissions"
date: 2010-04-06
forum: General Help
---

### Post by johnathanamber on 2010-04-06
Hello everyone,

I hope and pray that you all had a safe and wonderful Easter Weekend!

I have seen this issue come up previously in the forum:
> 
gpg: external program calls are disabled due to unsafe options file permissions


But the resolutions previously posted have not worked for me:
> 
sudo chmod 700 ~/.gnupg
sudo chmod 600 ~/.gnupg/*


I still get the following errors:
> 
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: WARNING: unsafe ownership on configuration file `/home/johnathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


I am trying to run this:
> 
#!/bin/sh
# download gpg keys
# run as root

sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys D19E31503603FC89 && gpg --export D19E31503603FC89 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys 651C88F37E3F6F85 && gpg --export 651C88F37E3F6F85 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys 66714E1023724DD8 && gpg --export 66714E1023724DD8 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys F3037F74D42BED5F && gpg --export F3037F74D42BED5F | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys 5DC3EDDDAAFF1F16 && gpg --export 5DC3EDDDAAFF1F16 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys F23E609A619BA177 && gpg --export F23E609A619BA177 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys 04508D5C1654E635 && gpg --export 04508D5C1654E635 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys FECEC7A25E1D6DC2 && gpg --export FECEC7A25E1D6DC2 | apt-key add -
sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys F693AC29CF84A40D && gpg --export F693AC29CF84A40D | apt-key add -


Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-04-07
Anyone have any ideas?

---

### Post by tlroche on 2010-05-12
> **johnathanamber said:**
> [heavily edited]

I have seen this issue come up previously in the forum:

> gpg: external program calls are disabled due to unsafe options file permissions

But the resolutions previously posted have not worked for me:

> sudo chmod 700 ~/.gnupg
> sudo chmod 600 ~/.gnupg/*

I still get the following errors:

> gpg: WARNING: unsafe ownership on configuration file `~/.gnupg/gpg.conf'

[when running]

> #!/bin/sh
> # download gpg keys
> # run as root

> sudo gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys D19E31503603FC89 && gpg --export D19E31503603FC89 | apt-key add -


I recently encountered the error message above. It results from sudo-ing, and can be disregarded, as explained in [this message]("http://marc.info/?l=gnupg-users&m=111170147828145&w=2"):

> David Shaw 2005-03-24 21:56:20
It means that the user you are running GPG as was not the owner of the
gpg.conf file.  That can be a security problem (as someone other than
you can manipulate it), so GPG is warning you about it.

Since you're running as root on purpose, it's presumably not a
security problem, but GPG doesn't know that.

HTH, Tom Roche <Tom_Roche@pobox.com>

---

### Post by lxyates on 2010-07-07
if you try to download the key as root, you will have this error (don't know why though)!

:guitar:

---

### Post by afrodeity on 2010-11-08
trying to upload a key and getting this error.

---

