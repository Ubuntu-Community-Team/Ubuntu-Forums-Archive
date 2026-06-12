---
title: "Tried to upgrade, /home still encrypted (whoops)"
date: 2010-07-10
forum: General Help
---

### Post by Slaskie on 2010-07-10
I have a dual boot WinXP / Kubuntu system. Recently, I tried to upgrade from 9.10 to 10.04. I have my Kubuntu partition set up with separate partitions for / , /home , and swap. Naturally, I wanted to wipe the slate clean, so I formatted / and left /home alone before doing the install. However, my /home partition was encrypted with the standard crypto that you get when you install. I just deleted the way in by wiping my / partition. Now all of my files are on my drive but encrypted. I do have the unencryption passphrase given to me when the hard drive was first encryped, so I am sure there is some way to get my files, but I am unsure how to apply it. Please help, and thanks very much in advance.

---

### Post by robsoles on 2010-07-10
Isn't there a relatively easy reference to the home folder that practically asks you for the encryption hash when you access the directory?


I would have to set up a Virtual Machine and get myself into similar circumstances to really help you - tell me you really need me to and I will if nobody beats me to a more helpful response before I can!

---

### Post by xifer on 2010-07-10
this is how my encrypted partition loads at boot - it prompts for passphrase

/etc/crypttab
```

# <target name> <source device>         <key file>      <options>
crypt-part        /dev/sda6       none            luks

```

and in /etc/fstab

```

/dev/mapper/crypt-part    /u1  ext4    defaults,errors=remount-ro,relatime 0    1

```

you may need this if you haven't already got it

apt-get install cryptsetup

but i'm not sure where it keeps the encryption keys - if they're lost you're stuffed.

HTH

---

### Post by robsoles on 2010-07-10
> **xifer said:**
> ...0

but i'm not sure where it keeps the encryption keys - if they're lost you're stuffed.

HTH

It keeps the keys in your hand, Slaskie says they have the key so I am sure we (i) can help them get their data back - just watch if you don't know better, what are you waiting for if you know better?

---

### Post by xifer on 2010-07-14
> **robsoles said:**
> It keeps the keys in your hand, Slaskie says they have the key so I am sure we (i) can help them get their data back - just watch if you don't know better, what are you waiting for if you know better?

Hi again.  didn't slaskie say he had the pass phrase?

Is that the same as the encryption key?  I didn't think so.  But please explain as I'd like to understand.

---

### Post by robsoles on 2010-07-14
> **xifer said:**
> Hi again.  didn't slaskie say he had the pass phrase?

Is that the same as the encryption key?  I didn't think so.  But please explain as I'd like to understand.


I made the assumption that they kept the encryption hash (fairly long number in hexadecimal) in a safe place and were now calling it the pass phrase - the fact that slaskie hasn't posted again seems to support my assumption in my opinion but I wish I had asked them if they meant they could remember their old password or that they went to the trouble of notating the encryption hash/key...


Have you installed Ubuntu and chosen 'require password to decrypt home directory and login' ??? - If not, you could just set up a VM and select that at the appropriate moment of installing and have a play with the resulting home-folder setup as an alternative user - you could also checkout the step on first login after installing at which a script executes and practically begs you to notate the encryption hash you will need to get at your files in your home directory if you replace your OS or it otherwises 'drops the ball'.


Asking is healthy - wondering is OK but without asking it may remain wondering!!!

---

### Post by Slaskie on 2010-07-23
Here is the thing: I am pretty much a Kubuntu / LinuxInGeneral noob. It seems to me that there should be some way to enter my long hexa-whatever key (big string of alphanumeric characters) to recover my data. I am writing this from a live Kubuntu 10.04 cd in my computer. All I need is to unlock my data once, then I can copy it over to a external hard drive, etc, and then format the encrypted partition and actually install Kubuntu. The live cd already has cryptsetup installed, and I messed around with it, but as I don't really know what I am doing in Konsole beyond the most basic of basics, I couldn't unlock my data. What would be a big help is if someone could tell me the exact command I would need to enter in Konsole to unlock my data. Or- any way to do it, really, but in step by step form :p. 
Here is some (maybe) pertinent information:

the encrypted partition shows up in gparted as /dev/sda7. Interestingly, although it is encrypted, gparted can tell the amount of free space and amount of used space on the partition.

Dolphin tells me that the encrypted partition is /media/disk. of course, when I try to enter my home folder, dolphin tells me "Could not enter folder /media/disk/myname". 

I have both my password for my previous Kubuntu installation (which I am pretty sure is useless now as I wiped the / partition) and the large alphanumeric unencrypt key given to me when I first encrypted my /home partition. I just need to know how to enter it to unlock my data.

I'd be happy to supply any more information if it is needed to unlock my files. Thanks very much for taking the time to read this and help :)

---

### Post by AlphaLexman on 2010-07-23
I would recommend making a backup of the 'disk image' from the partition your /home directory was on. Look into the command 'dd' and use /dev/sbd1 as your input file, or whatever naming structure points to the proper device. dd can copy the actual blocks of your disk, not just the files.

---

### Post by robsoles on 2010-07-23
Making a back up of the encrypted partition is a good idea but I read that you had it on /dev/sda7 and not /dev/sbd1.

Using the LiveCD you could make a partition on a new/seperate drive (including connected by USB, albeit slower perhaps) which is a size match for the encrypted partition and then get it's /dev/ address - if it's dev address was /dev/sdc2 for example the following dd command in terminal will back it up

```
dd if=/dev/sda7 of=/dev/sdc2
```
but you want to make sure that the encrypted partition is still on /dev/sda7 when you boot with an extra drive in the system!


That's a pain in the neck that the whole partition is encrypted, I have only ever made my home directory encrypted and so /home is mounted in a partition of it's own and so a LiveCD should allow me to access my home directory if I need to by showing me something to double click in nautilus that will then ask me for my encryption hash to open it.


I am tempted to say that nautilus (file-manager) from a LiveCD should show you the encrypted partition as an unmounted reference under ''places'' and selecting it from there should go on to prompt you for your encryption hash and then mount it for you if you've got it right - again about my not having encrypted a whole partition though. Actually, I have used palimpsest to make encrypted partitions and the behavior is as the start of this block of text and that is where I am getting the idea from.

If that just isn't like that from your LiveCD please say so and I will try harder to come up with something I've tested in terminal (in a VM :)) to post back with.

---

### Post by xifer on 2010-07-26
> **Slaskie said:**
> It seems to me that there should be some way to enter my long hexa-whatever key (big string of alphanumeric characters) to recover my data. I am writing this from a live Kubuntu 10.04 cd in my computer. All I need is to unlock my data once, then I can copy it over to a external hard drive, etc, and then format the encrypted partition and actually install Kubuntu. The live cd already has cryptsetup installed, [...]

I have both my password for my previous Kubuntu installation (which I am pretty sure is useless now as I wiped the / partition) and the large alphanumeric unencrypt key given to me when I first encrypted my /home partition. I just need to know how to enter it to unlock my data.

I'd be happy to supply any more information if it is needed to unlock my files. Thanks very much for taking the time to read this and help :)


Check this link 

[http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions](http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions)

Create a text file with your old encryption key, say keyfile.txt
then I think the command you are after is
```

cryptsetup create --key-file keyfile.txt e1 /dev/sda7

```

---

### Post by xifer on 2010-07-26
> **robsoles said:**
> 
That's a pain in the neck that the whole partition is encrypted, I have only ever made my home directory encrypted and so /home is mounted in a partition of it's own 

Misplaced confidence.  If only /home is encrypted then your system is in no way secure.

---

### Post by robsoles on 2010-07-26
I disagree - It's only as readable as the encryption in use is crackable and ultimately all encryption is crackable, just a matter of when.

/home on own partition encrypted - no.

/home/user within above partition encrypted using standard stuff Ubuntu 9.10 was ready to install with - yes.


Tell me just how my home folder '~/' is crackable that can't be applied to anything using crypt-fs and I will find a suitable hat and eat it!

---

### Post by xifer on 2010-07-26
> **robsoles said:**
> I disagree - It's only as readable as the encryption in use is crackable and ultimately all encryption is crackable, just a matter of when.

/home on own partition encrypted - no.

/home/user within above partition encrypted using standard stuff Ubuntu 9.10 was ready to install with - yes.


Tell me just how my home folder '~/' is crackable that can't be applied to anything using crypt-fs and I will find a suitable hat and eat it!

encryption is useless unless properly managed.

e.g. obtain data from swap partition.  If you don't know how to do that I'm not going to publish how here.  You need to encrypt everything.  But you can't do boot so you should carry that on you on a usb for example.  Or use checksums to find if anyone tampers with your initramfs.

check this link
[http://www.wzdftpd.net/blog/index.php?2009/10/28/44-implementing-the-evil-maid-attack-on-linux-with-luks]("http://www.wzdftpd.net/blog/index.php?2009/10/28/44-implementing-the-evil-maid-attack-on-linux-with-luks")


do you want ketchup with that?

---

### Post by robsoles on 2010-07-26
All encryption is ultimately crackable - even if you have your boot drive with you your remaining data will ultimately become, if not already, crackable by 'such and such' an effort.

Even an entire drive (be it SSD/Flash big or small, SATA via USB in a cage or whatever) encrypted using a long pass-phrase will ultimately be cracked, even where no OS anywhere has recorded the key/passphrase for the user - whether the intruders use brute-force dictionary attacks like a thousand computers for a thousand hours or just electrocute you for however long it takes to make you give it up, or even just make a tiny hole in the wall behind you high enough and angled enough to see your keyboard for next time you unlock your drive.

It is more likely (unless you are talking about a business environment) that your drive will be erased by the buyer that gets it off the drug-addicts that steal it from your house with simply the briefest attempt to get at your data.

Talk about thread-jacking, I hope your #10 does it (as I expect it ought) for Slaskie.

No, I'll pass on the ketchup, thanks anyway.

---

### Post by xifer on 2010-07-26
> **robsoles said:**
>  
No, I'll pass on the ketchup, thanks anyway.

whatever.  I've no time to debate whether you should eat that hat or not.  The point is if you're going to do it - do it properly or it's a waste of time.  Like you are wasting your time by only encrypting your home partition. 

This is the point I need to make for the OP.  Even with my 30 yrs experience of software dev I am on a learning curve here as I prepare my next machine to have as compete protection as I can manage.

BTW 1000 computers for a thousand hours is not enough...

---

### Post by robsoles on 2010-07-26
I'm am the IT admin and production manager for a small Electronics company.

Please consider just encrypting a single HDD in it's entirety and do not use it for /home /boot /root or any other 'naturally' mounted part of your file-system - don't allow your file-system to record the key/passphrase when you mount it.

Just mount it when you need it and be aware of prying eyes and how secure this drive is on whatever premises you take it to - it is honestly only a matter of time, you should see what cloud computing is doing to wpa and wpa2 security these days...

---

### Post by xifer on 2010-07-26
[QUOTE=robsoles;9638012]I'm am the IT admin and production manager for a small Electronics company.

/QUOTE]
so you should know that not everyone's needs are the same.  I need to have a secure installation... an encrypted home partition is not secure, one single encrypted device is not secure.

---

### Post by robsoles on 2010-07-26
Would you mind explaining how 'one single encrypted device is not secure' yet you feel you can secure your OS by taking your /boot with you on a USB? Isn't your OS on a single device? Perhaps it's a group of devices in an LVM or RAID# setup - doesn't that look like a single device to the cracker as well?

[COLOR=Red]EDIT: Would you start your own thread to explain this to me if you really can?[/COLOR] Link to it below by all means but I think Slaskie's request for help thread here has probably become convoluted enough with our argument! (Also, invite me to it with a PM to make sure I notice! ;))

If you encrypt your entire system, bar /boot which you keep on a USB stick around your neck, and something goes wrong and your system becomes unbootable/unstable you are in a much riskier position of losing all your data than my employer is IMHO.

Not many can tell you what commands to issue from a LiveCD's terminal to recover and you will probably need to refer to a written record of your encryption hash due to it being too long and complicated to remember without help of a passphrase wrapper. That written record sort of breaks the point, doesn't it?


I think you really should look at palimpsest and the encryption it offers for partitions, I will be genuinely surprised (but not horribly upset or anything) to have anyone prove that it is more crackable any easier than the way you propose to set up your system is.


Hey Slaskie, have you got your data back yet?

---

### Post by xifer on 2010-07-26
> **robsoles said:**
> Would you mind explaining how 'one single encrypted device is not secure'

see above note on swap and initramfs vulnerability.

This is not an argument.  The point of a discussion is not to win or lose but to learn.  That's why I'm here.

---

### Post by robsoles on 2010-07-26
You would have to leave the portable HDD I am recommending with the machine that is compromised or not recognise that it was compromised before using it to access the portable drive again.

[COLOR=Red]Sure, swap space may contain some snippets, or larger chunks, of the data depending on what you did with your data and if you don't do anything to scrub it before you shutdown - thanks for making me think of that, I'll look into what is happening to relevant swap space at work when I get there tomorrow.[/COLOR]

[COLOR="Blue"]OK, it's "tomorrow" and I've re-examined my setups - I am more concerned about our equipment being stolen or an insider being malicious toward the company in other ways than what the swap space contains after sensitive company data is accessed at a large enough scale to sample the potential problem.[/COLOR]

A discussion can be termed as an argument and an argument can be had as a learning exercise - I'd have thought most programmers would know what the word argument can mean.

---

### Post by xifer on 2010-07-26
> **robsoles said:**
> You would have to leave the portable HDD I am recommending with the machine that is compromised or not recognise that it was compromised before using it to access the portable drive again.

A discussion can be termed as an argument and an argument can be had as a learning exercise - I'd have thought most programmers would know what the word argument can mean.

with luck the OP will mark this thread solved and this tedious discussion will stop.  I'd rather call it a discussion not an argument.  Make whatever swerves or slurs you need - it makes no difference to me.  But do yourself a favour and read about how you really need to encrypt swap as a minimum to preserve secure access to any device ever mounted on your computer.  For me hiding a usb is a little easier than hiding a HDD.

if you wish me to explain how to obtain information from swap or anything else then feel free to email me 

xiferzeitgeist ''at'' gmail.com

you never know - i might learn something.

---

