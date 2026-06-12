---
title: "I am going to kill myself..."
date: 2006-04-19
forum: General Help
---

### Post by tokez on 2006-04-19
since XGL wont work yet runs perfectly on the LIVE CD.

I have tried every guide  I could find, reinstalled Breezy numerous times, had my brother try to install it (he successfuly did it on his breezy) and failed, and tried to install Dapper which does not work either.

AHh!

Radeon 9700 Pro (R300) :P

---

### Post by PapaWiskas on 2006-04-19
I normally dont criticize what people say.  But speaking from a tragic experience that I will never forget, the title of your post is greatly misleading and very disturbing.  

But that is just my opinion, and me being over sensitive I guess.

Sorry, maybe I shouldn't have said anything, but I could not help it.

BTW, I hope you resolve your issue, I wish I could help.

---

### Post by Blunts on 2006-04-20
As you did not explain the installation steps you tried I cannot elaborate much to help you, but this seems to cover every base for me.
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

---

### Post by Jason_25 on 2006-04-20
Use dapper, and tell us the specific problem you run into and the guide you used.

---

### Post by dg_w on 2006-04-20
As the last poster said..

If you rearly want to use XGL and Compiz then use dapper, I have installed it many times for people now ,, What graphics card do you have ? Nvidia or ATI ?

**_For Nvidia_**
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)
_**For ATI:**_
[http://www.dragonfyre13.com/TimWiki/InstallingXGLAndCompiz](http://www.dragonfyre13.com/TimWiki/InstallingXGLAndCompiz)

Both should "just work"  :)
Rember:

Fresh install Dapper
un-comment out all the repos
you may wish to add

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

sudo apt-get update
sudo apt-get dist-upgrade

then follow the instructions for your card above :)

Good luck and let us know ..... No need to kill yourself rearly  :)

---

### Post by tokez on 2006-04-20
[QUOTE=PapaWiskas]I normally dont criticize what people say.  But speaking from a tragic experience that I will never forget, the title of your post is greatly misleading and very disturbing.  

But that is just my opinion, and me being over sensitive I guess.

Sorry, maybe I shouldn't have said anything, but I could not help it.

BTW, I hope you resolve your issue, I wish I could help.[/QUOTE]

:grin: Sorry about that one but I have done just about everything. I even installed Dapper Drake on my computer (fresh) and it doesnt boot into the GDM. The only way for me to even get into the bash command line is to run into recovery mode and CTRL+C when it stops running commands.

Maybe there is a problem with my Dapper CD or perhaps it conflicts with my hardware. I run on an ATI Radeon 9700 PRO (R300). The entire install goes through without flaw and when I try to boot into it, when it *SHOULD* load into the GDM, the screen goes black. CTRL+ALT+BACKSPACE doesnt work, CTRL+ALT+F1 doesnt work.

As said, it could be a flawed CD ... but it did the same thing when I had a fresh breezy install and changed the sources.list to accomodate Dapper and ran apt-get update, apt-get dist-upgrade.

Cant fix multiple things at once, so if anyone has an idea about the Dapper install, please holler :P

(PS: Sorry again for thread name :P:P:P:P:P)

---

### Post by testube_babies on 2006-04-21
There should be a "Verify CD Integrity" (or something like that) option on the Dapper CD when you first boot to it.  I found that when I couldn't start GDM on my Dapper install it was because x was poorly configured.  Check out you /etc/X11/xorg.conf to see if it's loading the correct drivers.  (As a nVidia user, I wouldn't know what the correct drivers are, so that's about as much as I can help.)

And, by the way, linux should not cause one to become suicidal.

---

### Post by bored2k on 2006-04-22
My first thought when I read the topic was "Oh great, UbuntuForums on CNN." .

---

### Post by megahertza on 2006-04-22
Keep on trying dude, I have a ATI Radeon 9600 se and i finaly got it to run fine.

---

### Post by ade234uk on 2006-04-22
I am just going to wait until Ubuntu 6 is officially released and then I know XGL is working. I dont have time to mess my machine up at the moment.

---

