---
title: "via unichrome driver"
date: 2006-04-15
forum: General Help
---

### Post by jeller on 2006-04-15
:( hi all,I have tried to follow some of the guides on here to install this driver [http://prdownloads.sourceforge.net/u...-7.gz?download](http://prdownloads.sourceforge.net/u...-7.gz?download) but cant,I have not got a glue what Im doing](*,) please can anybody post a howto to install this driver and get my graphics card working,at the moment its set at 1024x768 the other 2 options are 800x600 and 640x480,the refresh rate is 60hz no other options,the file above I downloaded to my desktop,I am running ubuntu 5.10

---

### Post by localzuk on 2006-04-15
The via driver is included in the next release of Ubuntu (which is currently in its finalisation stages and will be released on June 1st). If you want to give the unstable version a try it seems to work fine for me.

However, if not, I would advise waiting until dapper personnally.

Also, you may wish to look at [http://www.viaarena.com/?PageID=2](http://www.viaarena.com/?PageID=2)

I'm not too sure about the unichrome.sourceforge.net project as it doesn't seem to have any up to date documentation.

EDIT: Also, I just noticed you posted this in the LiveCD version - I do not think you will be able to install extra drivers in this version as it is ran from CD and memory. I would advise, then, that waiting for Dapper to release is your best option.

---

### Post by jeller on 2006-04-15
[QUOTE=localzuk]The via driver is included in the next release of Ubuntu (which is currently in its finalisation stages and will be released on June 1st). If you want to give the unstable version a try it seems to work fine for me.

However, if not, I would advise waiting until dapper personnally.

Also, you may wish to look at [http://www.viaarena.com/?PageID=2](http://www.viaarena.com/?PageID=2)

I'm not too sure about the unichrome.sourceforge.net project as it doesn't seem to have any up to date documentation.

EDIT: Also, I just noticed you posted this in the LiveCD version - I do not think you will be able to install extra drivers in this version as it is ran from CD and memory. I would advise, then, that waiting for Dapper to release is your best option.[/QUOTE]


:) Thanks for the reply,I just want to try and get this graphic card to work,Ihad a look at the via website but all the drivers are for other distro's,How do I install a driver for onboard graphics,I am not ruuning the live version of ubuntu its installed on my hard drive along with 98se(just in case there was any confusion over which os I was running)please help](*,)

---

### Post by kaykills on 2006-04-16
funny how this is being talked about.... I installed Gentoo on my box and I cannot get the system to recognize my S3 Unichrome onboard graphics card.  I have spent two weeks on the issue.  I was considering trying Ubuntu because I am sick of this problem.  I may just need to try a different distro.... better yet, maybe I should buy a new graphics card.

---

### Post by localzuk on 2006-04-16
The via site contains a 'Not Distribution Specific' version - this should work. I would still suggest using Dapper though or waiting.

---

### Post by phyre-x on 2006-04-17
now i cant wait until june if theres going to be a new ubuntu release, i tried via driver but get a nice error so best i wait :D wonder if they're going to include an idiot guide to getting my soundcard working too, would be nice .

---

### Post by paloyme on 2006-04-19
Hi everyone, im new at this, just started weeks ago, and also still having this predicament, too. (having no idea how to install the drivers)

Couldn't someone who knows how to install this just try to install this? I tried installing the drivers from the via site by using 

sudo apt-get install viafb-install

but i only get this message 

user01@ERI04:~/Linux-FBDev-kernel-bin_20050726$ sudo apt-get install viafb-install
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package viafb-install

the .tgz folder is located in my desktop

I really have no idea how to do this, the sudo command i tried was just taken from a "how to install nvidia..." thinking that maybe this could work with unichrome too... do i need to transfer this tgz folder or the files within to a specific folder?

the readme file included with the driver is a headache... what does "building a viafb module" mean?

localzuk, when you said to use dapper, did you mean that it is simply just not possible to install this driver with breezy? 

hopefully somebody could point me to an understandable guide, all this sudo apt-get is driving me nuts.  i dont mean to bitch around with a frustrating installation, i hear its really pretty common when trying to install something on linux... but if only someone has the patience to share their linux  wisdom in installing this driver, i would gladly receive it:)

the reason why i want this driver installed so badly is because of the refresh rate of 61Hz at 1280x1024 which is killing my eyes:(

---

### Post by Tomy on 2006-04-19
Don't bother with the driver from the via website. Also the via driver from the unichrome project on sourceforge is not the one used by Ubuntu.

Ubuntu uses the via driver from xorg and you can find the most current drivers at:

[http://dri.freedesktop.org/snapshots]("http://dri.freedesktop.org/snapshots")

The development of these drivers is done at:

 [www.openchrome.org]("http://www.openchrome.org").

Getting the via (unichrome and unichromePro) driver to work properly on Breezy is not easy. Install Dapper. If you wait untill the Dapper beta is out on April 20th you will have the final Dapper minus some bug fixes and it will be better than Breezy from the day you install it. You will save yourself countless hours trying to get the via driver working on Breezy.

After you have upgraded to Dapper you may still not have the via driver working properly but it is much easier to fix. Post your questions on the Dapper forum and you will get more help than you will on this forum.

Tomy

---

