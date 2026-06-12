---
title: "Create My Own Live CD"
date: 2011-06-15
forum: General Help
---

### Post by linux_trojan on 2011-06-15
I am creating an application using Gambas.  I want to create my own Ubuntu Live CD and have this application on the Desktop.  Is there a fool proof, easy, point and click application that will allow me to create this type of Live CD?  I think all I need on the CD is gedit and open office and firefox.

---

### Post by kroq-gar78 on 2011-06-15
Yes, in fact, there are two (it depends on what you want to do):

Remastersys (check here for a tutorial: [http://www.psychocats.net/ubuntu/remastersys):](http://www.psychocats.net/ubuntu/remastersys):) pretty sure it creates an image of your current system and turns it into an Ubuntu ISO that's bootable.

UCK (UBuntu Customization Kit; [http://uck.sourceforge.net/):](http://uck.sourceforge.net/):) You manually customize which packages/programs are on the disk. Now, I'm not sure how to move/install your program onto the CD (you can manually customize it through both the command line/terminal and Synaptic package manager), but if its online (on the webz) I'm guessing you can retrieve it through wget.

Hope that helps.

Sincerely,
kroq-gar78

---

### Post by linux_trojan on 2011-06-15
Would it be possible to run the Ubuntu Live disk, download the Uck *.deb package, run Uck and let Uck use the Live CD info to create another Live disk?

---

### Post by inameiname on 2011-06-15
I've never heard of that being a way to do it. I suggest just using Remastersys. It works wonders, and incredibly easy. Just install your live cd, install remastersys, add your Gambas application, backup, and voila, you have yourself a custom live cd.

Unfortunately, you will have to first install the original live cd to 'update' it to your custom one. I believe your question was if you could simply update the disc without installing it first.

---

### Post by linux_trojan on 2011-06-15
> **inameiname said:**
> Just install your live cd, install remastersys, add your Gambas application, backup, and voila, you have yourself a custom live cd.

Unfortunately, you will have to first install the original live cd to 'update' it to your custom one. I believe your question was if you could simply update the disc without installing it first.

Yea, I am not sure what you mean by "Install the Live CD"?  You mean install it to my hard drive?  I am already running Ubuntu.  

What I meant originally was, I have 2 DVD/CD drives.  I could run the Live CD on one drive, down load Uck, then burn the Live CD with my application program to the second DVD/CD drive.  Is that possible?

I am a little confused.

---

### Post by inameiname on 2011-06-15
Sorry about that. If you are using Ubuntu, then of course you already have it installed. I just meant install the ISO you downloaded from Ubuntu's website first. You cant easily update that ISO with your own tweaks, so best to first install it. Which you've done already. Moving on now...

Anyway, now I'm a bit confused. 

"What I meant originally was, I have 2 DVD/CD drives.  I could run the  Live CD on one drive, down load Uck, then burn the Live CD with my  application program to the second DVD/CD drive.  Is that possible?"

Let's see...if you were to run the original live cd that you got from Ubuntu's website, you'd have to restart the computer and run Ubuntu off the live cd, not the computer. Once logged into your live cd, then yes, you can download Uck and do what you want, but that really has nothing to do with the Ubuntu on your hard drive. 

I think you are thinking the original live cd plays a part in the custom one you want to create. Once you've installed it to the hard drive, it's done with. Put it aside. 

At least with Remastersys, how it works is to install it and its repos, like this to the Ubuntu on your hard drive:

Add this to your sources.list in /etc/apt/:

For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
  deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

then open a terminal window and paste this:

sudo apt-get update
sudo apt-get install remastersys


OR just install the deb I downloaded from there in the tar.gz file below

...then install Uck and make sure you have your application installed, where you want it and all that, and then run Remastersys. It'll create the Live CD in ISO form in a folder in /home/remastersys, and then you just burn that ISO to disk, and that's that.

---

### Post by linux_trojan on 2011-06-15
I guess I am under the impression that Remastersys copies the OS from the / partition and burns it to make the Live CD?  I dont want to let people know what all I have installed, I wanted a generic  Live CD to pass out.  Also, my Desktop is on /home, different partition.

Unless Remastersys creates the Live CD from repositories online?

I think I almost have my mind around this.

---

### Post by inameiname on 2011-06-15
Ok here, let me see if I understand. You want Remastersys to make a generic Live CD, much like the original, but with the added program, but WITHOUT your home folder and customizations? Am I correct here?

If so, you can do that with Remastersys. It gives you the option to make an actual FULL backup, including all of your home folder stuff and customizations for all programs, or a LIVE CD backup, of your operating system, which does not put on the home folder, or any customizations. What it does do is adds the extra packages you installed, such as your application.

As far as what you don't want others to know you have installed, I don't quite get you here. Like I said, if its files/folders in your home directory, just do the LIVE CD backup option and you are fine. But if its the actual packages you are worried about, then you may have a problem as they will all be there for each and every Live CD you make. Though, isn't the extra packages/applications you install what you want on the disc to share?

Finally, a particular desktop icon will be in your home folder, so I'm not sure if you choose the LIVE CD option it will be there. But the application will be installed so it should be in the Main Menu.

All Remastersys does is copies your folders you have, excluding those you dont want (such as your /home/your_username folder), and then automatically puts them inside an ISO that resembles an original Ubuntu live cd. Only what you've installed beforehand from repositories online will be there.

---

### Post by linux_trojan on 2011-06-15
I think I understand now.  I have lots of programs like Seamonkey, Galleon, VMware, Kino, Xine, MPlayer, lots of stuff thats kinda irrelevant to the application.  I really just wanted a stripped down version of Ubuntu, just Gedit, Firefox, and Open Office -- and my application.

But I think I understand now, so I will use it.  Thanks for the input.

---

### Post by inameiname on 2011-06-15
No prob.

Usually what I do is to make a fresh installation of Ubuntu, and once installed, add/remove whatever applications and whatnot, and then use Remastersys to make an updated Live disc. In my case, I use Full backup to back up everything, which essentially gives me a complete image that I have when necessary. 

Anyway, if its truly a stripped down version you want, then to avoid those extra packages a fresh install on the computer or another computer if possible would be best choice.


I'm sure with a lot more research and greater understanding of how it all works, you might be able to manually add things to the original Live CD. But that's way beyond me on how to do that. hehe

---

### Post by kalaharix on 2011-06-15
Hi

Just another point. You don't have to have a full installation of Gambas. It is a bit of a fiddle but you can create an installation package (i.e. to install on a raw Ubuntu install) which will consist of Gambas runtime plus the tokenised (i.e. sort of compiled) version of your program. This would have a name like myProg.gambas

---

