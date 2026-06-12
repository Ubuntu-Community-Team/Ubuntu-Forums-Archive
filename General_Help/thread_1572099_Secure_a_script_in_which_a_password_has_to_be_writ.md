---
title: "Secure a script in which a password has to be written"
date: 2010-09-10
forum: General Help
---

### Post by MrMotski on 2010-09-10
Hey guys,

I'm writing a script that automates a few commands like tarring and zipping a folder, and then uploading it to a web host. This web host provides a perl script to do that but to call it, the password to the web host has to be written out explicitly in the command line (like this: perl Upload.pl username password). Offcourse this is a situation i want to avoid.

Any ideas as how to deal with this? The options I thought of  are 
1. Making a prompt like when using sudo, which does not show what you're typing and then passing this input to the command.
2. Encrypting the script so the password can't be read in raw text (but then I"m not sure if i can run the script)

Probably some novice questions but hey, im just getting started with this! :)

---

### Post by ubulal on 2010-09-10
Just hack Upload.pl to have the username/password hard coded inside the script itself and make it user-only readable.  When you're concerned about other users logged into your own machine sniffing the password by watching ps(1) output, then that's enough.  If the upload is by FTP then the password is transfered in clear text over the network anyway.  For maximum security use sftp/scp with public key authentication exclusively, if your hosting provider supports it.

---

