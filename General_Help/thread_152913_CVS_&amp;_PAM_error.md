---
title: "CVS &amp; PAM error"
date: 2006-03-30
forum: General Help
---

### Post by StinkyPete on 2006-03-30
Hello - I've googled this to death, here's the problem.

* Fresh Ubuntu 5.10 install
* Install cvs and cvsd packages
* Configure as per [http://konni.com/archives/3]("http://konni.com/archives/3")
* Then I configure my CVSROOT and try and login with both "cvs login" and "cvs -d .... login"

I always get the following error:

[COLOR="Orange"][FONT="Courier New"]PAM start error: Critical error - immediate abort
Fatal error, aborting.
cvs [login aborted]: unrecognized auth response from localhost: pam failed to release authenticator
[/FONT][/COLOR]

I have tried editing the cvs.conf to set PamAuth and SystemAuth to 'no' 
I've looked at my PAM config files and see nothing wrong.

As anyone got any ideas (am I just bad at googling)

--Peter

---

