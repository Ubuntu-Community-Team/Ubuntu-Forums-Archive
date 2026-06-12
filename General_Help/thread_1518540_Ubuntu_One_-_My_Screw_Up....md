---
title: "Ubuntu One - My Screw Up..."
date: 2010-06-26
forum: General Help
---

### Post by dvlchd3 on 2010-06-26
I screwed up with Ubuntu One.  Since I did a fresh install of 10.04 from 9.10 on both my laptop and my desktop, I had two device entries for each machine in Ubuntu One.

In an attempt to clean this up a little, I deleted the older ones, however, this seems to have screwed everything up.  If I open Ubuntu One's preferences, I get an error: "Got empty result for device list". Also, Ubuntu One does not synchronize anymore.

Since there is no "add computer" link anymore, I'm not sure how to add a computer that was already added...but then removed...

I tried doing a complete reinstallation of Ubuntuone:
```

sudo apt-get --purge autoremove ubuntuone-client && sudo apt-get install ubuntuone-client
```

However, I am still having the same issue.  Is there a way to force Ubuntu One to add a computer on startup?

---

### Post by mve on 2010-07-02
I have exactly same problem. Could some one tell us where is the Ubuntu One account information saved in the computer and how to remove it?

---

### Post by duanedesign on 2010-08-06
In order to reauthorize your computer you need to make sure there are no leftovers from the previous authorization. 

   1. Quit the Ubuntu One client (if it is open)
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Karmic:Applications->Internet->Ubuntu One Lucid:Me Menu-> Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

If you do not see the 'Add This Computer Button in step 9 see [here]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?")

---

### Post by mve on 2010-08-29
> **duanedesign said:**
> In order to reauthorize your computer you need to make sure there are no leftovers from the previous authorization. 
[/URL]

Thank you. After this I was able to add my laptop again in Ubuntu One without reinstall.

---

