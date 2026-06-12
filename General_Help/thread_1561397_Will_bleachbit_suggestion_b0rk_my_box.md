---
title: "Will bleachbit suggestion b0rk my box?"
date: 2010-08-26
forum: General Help
---

### Post by t0p on 2010-08-26
I desperately need to free up some disk space while awaiting better hardware to arrive.  Messing with bleachbit's previews, I had a look at what would happen if I went for the *Localizations* option and got the preview you can see in the attached text file.

I had a look through the list, and the files all seem to be related to languages I don't use (I use English).  But it's a long list and I may easily have missed something.

Would telling bleachbit to do its thang be okay?  Or would it kill my machine.

Also, I have had *localepurge* installed for a very long time.  Why is this "localization" stuff still around?

---

### Post by inameiname on 2010-08-26
I've never had a problem with bleachbit, and I check everything available, except Firefox-Places (as that removes bookmarks in it), and System-Free Space and System-Memory (as the one just erases and very time consuming and the other is experimental). 

So again, never bothers me or borks mine.

Oh, and one thing bleachbit OR localepurge doesn't seem to remove on my computer is config files. I remove those using Ubuntu-Tweak, which is another Ubuntu must-have.

---

### Post by t0p on 2010-08-26
Okay, inameiname, I'm gonna do it.  But if this kills my computer, it's gonna come back and haunt you!  :p

---

### Post by t0p on 2010-08-26
Well that *appears* to have worked just fine.  Lotsa freed-up space.

Thanks!!

---

### Post by inameiname on 2010-08-26
Haha, well hopefully it won't. ;)

I guess there's always a possibility, as what is installed on mine and the bleachbit cleaners used aren't necessarily the same as on yours. So there's a chance those programs I never use nor have cleaners for might be bad, idk.

Also, on a side note, don't forget to add bleachbit-bonus from their website. It adds a few more cleaners.\

Oh, and don't forget that with bleachbit, you can run it two ways, as there should be two bleachbit items in your applications menu. One is for root, and the other is for your home folder, and both clean. I also 'sudo bleachbit' in the terminal to ensure I delete those files that give me a permission denied in the normal bleachbit run.

---

### Post by inameiname on 2010-08-26
Woosh. Glad it worked fine for ya.

---

### Post by Andrew.Z on 2010-08-27
> **t0p said:**
> Also, I have had *localepurge* installed for a very long time.  Why is this "localization" stuff still around?

Because BleachBit is more thorough than localepurge: you may want to read ["Free much more disk space than localepurge"](http://bleachbit.blogspot.com/2009/07/free-disk-space-localepurge.html)

---

### Post by kismul on 2011-01-16
> **t0p said:**
> Well that *appears* to have worked just fine.  Lotsa freed-up space.

Thanks!!


Following this, I too used bleachbit to get lots of freed space - but not as much as I expected.  

When I ran the software, it promised me about 1.4gb of freed space.  I got a little over 540mb and a lot Error messages in the file listing, along the lines of (for example):

[COLOR="Red"][Errno 13] Permission denied: '/var/cache/apt/archives/usb-creator-common_0.2.12_all.deb' /var/cache/apt/archives/usb-creator-common_0.2.12_all.deb[/COLOR]

Can anyone enlighten me as to what the problem was here?  Did I do something wrong?

---

### Post by Frogs Hair on 2011-01-16
You need to run bleachbit as root other wise it can't access all ares for clean up.

---

### Post by Timmer1240 on 2011-01-16
I use it all the time never had a problem with it works great

---

### Post by cipherboy_loc on 2011-01-16
Thanks for the suggestion, am trying it out now.


Cipherboy

---

