---
title: "Creating a custom ubuntu ISO"
date: 2010-05-21
forum: General Help
---

### Post by mailtome on 2010-05-21
Hi,
I want to create a custom ubuntu ISO (This ISO will contain all the packages with the latest updates released till date). How should I go about it?

---

### Post by mikewhatever on 2010-05-21
Use remastersys.
[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by _Mark_ on 2010-05-21
Just to let you know, the apt source mentioned in the article no longer works it is now this

```
For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
#  Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

```

---

### Post by mailtome on 2010-05-24
Thanks for the replies. Rematersys is a cool tool but its not the way I am looking for creating the updated ISO.
Can't I take the pristine ubuntu ISO, download the updates from some ubuntu update repositories, and re-create the ISO?

---

### Post by remys on 2010-05-25
Hello,
I tried to create an iso with remastersys and after burning it to a cd i was not able to boot it as a live distro...is anyone managed to do it?

---

### Post by inameiname on 2010-05-25
To mailtome:

I'm guessing you are talking about downloading the whole repos, not necessarily installing them, and then backing that who thing up in some iso...is that right?

Warning though, it'll be around 40-60 GBs I believe.

Of course, if that isn't what you want, and you mean wanting something to basically back up a fresh install of an Ubuntu ISO, but with whatever updates and the few tweaks you may or may not include, then Remastersys is definitely the program to go.

To remys:

What exactly is your issue? Is it popping up an error and won't boot? Are you using the correct Remastersys version for your Ubuntu installation?

Oh, and you should definitely check out the Remastersys forum for help too if we can't resolve things for you. The guy that makes the program goes out of his way a lot with helping those that use his product. He's personally helped me with a few issues, one also being not able to boot into the live distro (as well as to install it).

[http://www.geekconnection.org/remastersys/forums/](http://www.geekconnection.org/remastersys/forums/)

---

### Post by remys on 2010-05-25
Thanks for your quick reply.
I get a can not find kernel error after burning the iso to a cd and try to boot it.
I tried three options Backup/Dist/Distiso and none of these worked.

Thanks a lot for the link.I ll check it!

---

### Post by philinux on 2010-05-25
> **remys said:**
> Thanks for your quick reply.
I get a can not find kernel error after burning the iso to a cd and try to boot it.
I tried three options Backup/Dist/Distiso and none of these worked.

Thanks a lot for the link.I ll check it!

I did 2 yesterday with no error, did you check the md5sums matched? How big were the iso's? Best as it says to close all other running apps and dont do anything while it's finished.

---

### Post by inameiname on 2010-05-25
Yeah, I agree with philinux. Also, is your kernel the standard one or did you try upgrading or downloading it elsewhere? I know that can cause issues for most of us who aren't experts on such.

---

### Post by philinux on 2010-05-25
> **mailtome said:**
> Thanks for the replies. Rematersys is a cool tool but its not the way I am looking for creating the updated ISO.
Can't I take the pristine ubuntu ISO, download the updates from some ubuntu update repositories, and re-create the ISO?

And what application are you going to use to recreate the ISO?

---

### Post by mailtome on 2010-05-25
@inameiname: You are some what correct. I do not need the entire repo. Just the main, and restricted. And only the latest version of the components. So I guess the size will come around 4-5 GB.
@philinux: mkisofs can be used to recreate the ISO. 
I have done something similar for centos, suse using: 
For centos: [http://nootech.wordpress.com/2007/12/11/build-a-custom-centos-5-install-cd/](http://nootech.wordpress.com/2007/12/11/build-a-custom-centos-5-install-cd/)
For suse: makeSUSEDVD [http://sourceforge.net/projects/makesusedvd/](http://sourceforge.net/projects/makesusedvd/)

---

### Post by jerenept on 2010-05-25
Ubuntu Customisation Kit seems cool to me. It's in the repos and you get to run synaptic within the iso.

---

### Post by mailtome on 2010-05-25
And, if it matters I will be customizing the server ISO.

---

### Post by mailtome on 2010-05-25
A problem that I see with this is:
When I install ubuntu, it does not asks me which packages I want to install (other than in server installation it asks for LAMP, openssh etc). 
Is there some file (or another method) to tell the installer to only install certain packages.

---

### Post by inameiname on 2010-05-26
To mailtome:

Maybe this will help too:

[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

Perhaps you can merely download all that you want, keep them handy, and then go from there. IDK.

---

### Post by tlacuache on 2010-05-26
This link was very helpful to me, if you really want to do it from scratch.

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by emarkay on 2010-06-17
In a similar manner I am looking for the same thing:

[http://ubuntuforums.org/showthread.php?t=1512104](http://ubuntuforums.org/showthread.php?t=1512104)

---

