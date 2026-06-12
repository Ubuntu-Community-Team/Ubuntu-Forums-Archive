---
title: "Gnome 2.3 and 3"
date: 2011-10-21
forum: General Help
---

### Post by zero2xiii on 2011-10-21
Hay all,

I am curious about this new Gnome version in 11.10. I am running ubuntu 10.04.4_32bit.

I want to know if I can upgrade to gnome 3?... Is all this 'issues' everyone is experiencing on ubuntu 11.10 due to gnome3 or due to some changes made in the new kernel?

I dont want to break my system. And it will be even more awsum if I can keep gnome 2.3 side by side with 3... Like selecting it during boot? oor at the login screen..

It this possible? What is the general feeling about only upgrading gnome? WIll this cause program issues or not.

Oh and can KDE be installed side by side with gnome? SO that it can be selected in log in if you want a KDE or Gnome session?

Thanks and Cherz

---

### Post by haqking on 2011-10-21
> **zero2xiii said:**
> Hay all,

I am curious about this new Gnome version in 11.10. I am running ubuntu 10.04.4_32bit.

I want to know if I can upgrade to gnome 3?... Is all this 'issues' everyone is experiencing on ubuntu 11.10 due to gnome3 or due to some changes made in the new kernel?

I dont want to break my system. And it will be even more awsum if I can keep gnome 2.3 side by side with 3... Like selecting it during boot? oor at the login screen..

It this possible? What is the general feeling about only upgrading gnome? WIll this cause program issues or not.

Oh and can KDE be installed side by side with gnome? SO that it can be selected in log in if you want a KDE or Gnome session?

Thanks and Cherz

The main issues people seem to have are with Unity which is a shell that Ubuntu are now using which happens to sit on top of Gnome 3 which is the new version of Gnome 2.  You can install Gnome 3 and use Gnome Shell instead of Unity.

Here is a link for Gnome 3 on 10.10 [http://blog.sudobits.com/2011/04/24/how-to-install-gnome-3-on-ubuntu-10-10-10-04/](http://blog.sudobits.com/2011/04/24/how-to-install-gnome-3-on-ubuntu-10-10-10-04/)

And yes you can run KDE alongside Gnome, though it often means a messy applications menu but you can choose between DE at Login

**Make sure you have backups or clones though before doing this ;-)**

---

### Post by zero2xiii on 2011-10-21
> **haqking said:**
> The main issues people seem to have are with Unity which is a shell that Ubuntu are now using which happens to sit on top of Gnome 3 which is the new version of Gnome 2.  You can install Gnome 3 and use Gnome Shell instead of Unity.


So if I understand you correctly, If I install gnome 3, I wont have unity UNLESS I install that seperately? I will then basicly still have the "classic ubuntu" desktop. Or I will have unity, but still have the classic ubuntu desktop option?

---

### Post by linuxinstalledfromhdd on 2011-10-21
Don't install Gnome 3 in anything other than 11.10 otherwise you are looking for big trouble.  Make sure you backup your entire system if you do. Only try Gnome 3 on 11.10 since that is the only time I have been able to get it to work successful.   And AutoLogin is not working in Gnome 3 on Ubuntu 11.10, just to be really clear about how buggy 11.10 is right now.

> **zero2xiii said:**
> Hay all

I am curious about this new Gnome version in 11.10. I am running ubuntu 10.04.4_32bit.

I want to know if I can upgrade to gnome 3?... Is all this 'issues' everyone is experiencing on ubuntu 11.10 due to gnome3 or due to some changes made in the new kernel?

I dont want to break my system. And it will be even more awsum if I can keep gnome 2.3 side by side with 3... Like selecting it during boot? oor at the login screen..

It this possible? What is the general feeling about only upgrading gnome? WIll this cause program issues or not.

Oh and can KDE be installed side by side with gnome? SO that it can be selected in log in if you want a KDE or Gnome session?

Thanks and Cherz

---

### Post by haqking on 2011-10-21
> **zero2xiii said:**
> So if I understand you correctly, If I install gnome 3, I wont have unity UNLESS I install that seperately? I will then basicly still have the "classic ubuntu" desktop. Or I will have unity, but still have the classic ubuntu desktop option?

Unity is a shell, if you install 11.04 or 11.10 then it is the shell used unless you install Gnome shell.

If you only install gnome 3 then you wont have Unity, Gnome and Unity are not related.

Your best bet is to run a Live CD/DVD/USB etc to test and try or use a virtual machine.

---

### Post by haqking on 2011-10-21
> **linuxinstalledfromhdd said:**
> Don't install Gnome 3 in anything other than 11.10 otherwise you are looking for big trouble.  Make sure you backup your entire system if you do. Only try Gnome 3 on 11.10 since that is the only time I have been able to get it to work successful.   And AutoLogin is not working in Gnome 3 on Ubuntu 11.10, just to be really clear about how buggy 11.10 is right now.

I have a 10.04 and 10.10 virtual machine runnings gnome 3 with gnome shell and runs very well actually for a VM, not that i used them, i just wanted to play.

and you dont install Gnome 3 into 11.10 as it is already Gnome 3.2

But as i mentioned above, use a VM or Live version for testing and dont mess up your main build

---

### Post by linuxinstalledfromhdd on 2011-10-21
In Ubuntu 11.10 you can have Unity, Gnome 3, anything you want.  It will break on 11.04 though..  I have had Gnome 3 break on 11.04 several times. Not worth the effort for what Gnome 3 has become - in my opinion too. They haven't even ported over the older GTK2 to GTK3 themes yet, so it still looks very bare to me.

> **haqking said:**
> Unity is a shell, if you install 11.04 or 11.10 then it is the shell used unless you install Gnome shell.

If you only install gnome 3 then you wont have Unity, Gnome and Unity are not related.

Your best bet is to run a Live CD/DVD/USB etc to test and try or use a virtual machine.

---

### Post by haqking on 2011-10-21
> **linuxinstalledfromhdd said:**
> In Ubuntu 11.10 you can have Unity, Gnome 3, anything you want.  It will break on 11.04 though..  I have had Gnome 3 break on 11.04 several times. Not worth the effort for what Gnome 3 has become - in my opinion too. They haven't even ported over the older GTK2 to GTK3 themes yet, so it looks pretty ugly right now still.

you are confusing Gnome 3 and unity.  Unity is a shell, it is always using Gnome 3 (3.2 actually) or do you mean Gnome Shell which is different

---

### Post by zero2xiii on 2011-10-21
Hay thanks for all the replies (and sooo fast),

I think I will somehow create an image of my current ubuntu 10.04 installation and run it in a vmware machine and then install gnome 3 and see what happens.. 

I used to love ubuntu due to the stability of it.. But seems like things are not as stable yet as it used to be. To many changes ontop of each other I guess.. 

But thanks again. Will see if I can test this and report back ;)

Cherz

---

### Post by linuxinstalledfromhdd on 2011-10-21
I talking about login sessions..  When you login you can change sessions.. You can select Gnome, Gnome Classic, Unity..  etc etc etc.. That's what I am talking about here..

> **haqking said:**
> you are confusing Gnome 3 and unity.  Unity is a shell, it is always using Gnome 3 (3.2 actually) or do you mean Gnome Shell which is different

---

### Post by haqking on 2011-10-21
> **zero2xiii said:**
> Hay thanks for all the replies (and sooo fast),

I think I will somehow create an image of my current ubuntu 10.04 installation and run it in a vmware machine and then install gnome 3 and see what happens.. 

I used to love ubuntu due to the stability of it.. But seems like things are not as stable yet as it used to be. To many changes ontop of each other I guess.. 

But thanks again. Will see if I can test this and report back ;)

Cherz

you can use clonezilla to make an image of your existing build and then you can clone that into a VM if you wish, the thing is it is not a true test as you will be using Virtualised hardware not the the real graphics drivers which is often the problem.

Do it for sure, but also try it on a USB with persistence for example so you can use real hardware.

I personally like gnome 3 with Gnome shell, mind you i also like Unity, i havent had a single problem with it to be honest.  Though now i am running Debian Unstable with Gnome 3.2 and Gnome shell for the time being

---

### Post by haqking on 2011-10-21
> **linuxinstalledfromhdd said:**
> I talking about login sessions..  When you login you can change sessions.. You can select Gnome, Gnome Classic, Unity..  etc etc etc.. That's what I am talking about here..

OK i was just clarifying for the OP, if you choose Unity you are still using Gnome 3 thats all i meant

---

