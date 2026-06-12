---
title: "What are some things I can purge?!"
date: 2011-03-27
forum: General Help
---

### Post by Vostrocity on 2011-03-27
Ubuntu has locked me out of the graphical system after I accidentally filled up my filesystem to 100% and then restarted. What are some common things I can safely delete and how would I do it through the command line (I am a noob)? I'm thinking perhaps there's a cache to clear or something like that?

---

### Post by cbowman57 on 2011-03-27
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean

That might get you back up & running, then install bleachbit and do some cleaning of your localizations and see what else needs to go.

---

### Post by Hedgehog1 on 2011-03-27
Vostrocity,

You first need to know that if you 'delete' anything using Nautilus (the GUI) while running the LiveCD/LiveUSB you will need to empty the trash can to free up the space.

Next - If you boot off the LiveCD/LiveUSB, you can copy larger items to a USB drive or a USB stick - this would save them, then delete the original on the hard drive (and empty the trash).

If you want to remove 'junk', please be careful.  Here are the keys to Pandora's box:

Boot off the LiveCD/LiveUSB. select 'TRY'.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

** -- this example assumes your Ubuntu parition is /dev/sda5.  If yours is other, please change the first line to match --**

Mount the hard drive Ubuntu partition:

```
sudo mount /dev/sd**a5** /mnt
```

Remove everything in the /tmp directory on the Ubuntu partition

```
sudo rm /mnt/tmp/* -r
```

I have to be honest - I would prefer that you do the 'copy things to a USB drive or USB stick and delete the originals (and empty the trash)'.  

***The Hedge***

:KS

---

### Post by Husker on 2011-03-27
Don't use the Computer Janitor.
I learned this the hard way.

---

### Post by Vostrocity on 2011-03-27
Thanks Hedge for the detailed instructions. I didn't have a Live CD handy so I just did <Ctrl>+<Alt>+<F1> at the login and did the cleaning cbowman said. That allowed me to log back in and amazingly gave me 2.4GB of free space. I did lose a few weird settings such as changed fonts and my Docky config. But those were easy enough to fix. :)

---

### Post by cbowman57 on 2011-03-27
Glad to read you're up & running again.

Are you going to be able to expand that partition or do you just need to do some housecleaning?

---

### Post by Vostrocity on 2011-03-27
Well, I was building and testing a bunch of different versions of a phone ROM, so that was what took so much space. I can easily delete all of those once I'm satisfied with one ROM.

---

