---
title: "Cant get 11.04 live usb to boot up, nor can I mount its encrypted home folder"
date: 2011-05-22
forum: General Help
---

### Post by cleerline on 2011-05-22
Hi there,
I created a live usb ubuntu (11.04) system on my usb drive.
I set it to have some persistant space.
I set the home directory to be encrypted (this was a mistake).

Anyway, this was about three weeks ago. Since then I have been doing some very important work on it that I cant afford to lose.

Yesterday when I booted up it asked for my password as usual but then came up with a load of errors about not being about to mount various directories. There was a word beging with ice.
It finished booting up but there were no menu items or task bars or anything. Just a blank ubuntu background graphic with the cursor. I shut the machine down and tried again. Same problem.
Panicing a bit I tried rebooting again. This time it asked me to create a pass phrase (a step I had foolishly skipped when I first set the machine up). I typed in a passphrase It then booted up but again no just an empty background with a cursor but nothing to click on.
So I rebooted again. THis time it again asked for a passphrase which I again entered. Same problem. Empty background with nothing on it.

I decided to give it one more try at booting up. This time i get to the screen where you select if you want to install or live boot. If I live boot I get the 11.04 booting splash screen with the four dots underneath and it gets no further. This is the state it is currently in.


I decided to try something different. At the screen where you get to choose between booting from the live usb and installing it I decided to install the system on my laptops hard drive.
This went OK, and botting from the laptop hard drive is fine.
So the linux image on that usb is OK i thought.

I then put the usb drive into my ubuntu 10.04 desktop (i idn't trust the 11.04 copy I had just installed on my laptop's hard drive). I used the ubuntu disk utility to check the usb filesystem and it comes back as having no errors.
I can look at the folders on the usb drive just fine. But obviously cannot access the home directory as it is encrypted.

Anyway, I ran fsck and it comes back with "there are differences between boot sector and its backup." about 500 differences are then displayed.
I tried the option for copying the backup to the original but it comes back with "Leaving file system unchanged". I tried this several times.
I tried running fsck in automatic mode but it came back with "not auto fixing this"

Now I guessed that I probably cant load up this encrypted file system without a passphrase. But I gave this: a try [http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

it fails on the line # mount -o bind /dev $D/dev with the message 

mount: mount point /media/chroot/dev does not exist

why am I getting that message when I have followed the instructions to the letter?

Anyway, I wondered if perhaps my usb port on my laptop was messed up so i tried booting the usb from my desktop. Same again. 11.04 splash screen and hangs there.

I think the only thing for me to do is trying to find out how to mount the encrypted home folder without the passphrase. Is this possible. That link I posted above seems to just require the username and password which I have.

Any ideas on how I should go forward? I really need this data...

Thanks

Cleerline

---

### Post by DBC1109 on 2011-05-22
I joined this today too.

Have been using UBUNTU for a year.

Have you made copies?

Then you can get aggressive ,

I still have not been able to boot to Win7, but I got most of my files,pics and videos off of Win7.

I reinstalled UBUNTU and one of the options was uninstall 11.04 & reinstall 11.04.

It asked if i wanted to import Win7 under my user.

If your files are not sensitive  send me a copy.
Dave

---

### Post by cleerline on 2011-05-22
Hi there, thanks for the reply.
Well, I can access the USB drive and look at the folders but I cant seem to mount the home folder. I have been through the tutorials but get stuck at certain points. Mainly the mounting sections. I have no clue about mounting.

Anyway, you mentioned windows 7, I used the encryption facilities built into that as well. It took around 16 hours to encrypt the hard drive (during which time I dared not use the machine) and then got stuck at 98%!!!!

And at that point it would not allow me unencrypt and start again!!
After about a month of effort it had encrypted the drive to 100% and I hastily unencrypted it, never to trust windows encryption again.

I thought linux might be different. But it looks like they have problems too.

I mean come on, the only thing I have done with that machine (which is brand new) is create a live USb stick. Clicked "yes please encrypt my home directory". Now 3 weeks later it refuses to boot?

And  what have I done with the machine to get it to this horrendous unbootable state? Run  nautilus, gedit and mine sweeper!

Linux cant handle running its own file browser, text editor and a 2d game?

Disappointing.

Sorry, I'm just a little bitter.

Linux encryption, so secure not even you can access your own data!

Never using encryption again.

---

