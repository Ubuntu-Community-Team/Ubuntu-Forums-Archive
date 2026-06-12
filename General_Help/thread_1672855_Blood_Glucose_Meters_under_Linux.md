---
title: "Blood Glucose Meters under Linux"
date: 2011-01-21
forum: General Help
---

### Post by pricetech on 2011-01-21
I'm posted recently about the One Touch meter, but I'm now looking at the Free Style and the Bayer Contour meters.

I'm curious if anyone has made any of the above work under Linux, preferably Ubuntu.

The Bayer Contour USB plugs directly into the USB port so no proprietary cable is necessary.  Their listed specs show that the software works under Windows and OS X, so maybe their headed in the right direction.

If I can access the data on the meter and make sense out of it, I should be able to at least put it in a spreadsheet even if I have to copy and paste or manually enter the data.

So, if anyone has made either of the above work, or knows of a brand name meter that will work, it would be helpful.

---

### Post by Jouke74 on 2011-05-04
I agree with all from the poster above me. I have been trying to get the Bayer Contour to work under linux Ubuntu for some time now, but all attempts failed miserably. The problem is that under Windows it simulates a COM port, while under Ubuntu this is a no go.

The Bayer Contour software also does not play nicely.

Best way to do it for now: 
1. Install Virtualbox and Windows XP virtual machine.
2. Install the Bayer software into the virtual machine.
3. Run the software from there allowing the USB filter in Virtualbox to directly port the Bayer meter to XP.

Note that even then sometimes the meter fails to port all data to the software. In that case (workaround): go to your personal info tab, change your gender from male to female and back, or the other way around, save settings (this will technically change your account). Reload the measurements by replugging the meter (sigh).

Once you have the Bayer.db file you can do anything with it as it is a simple SQlite database (note this is not stored in the meter, but made by the software).

Install the Sqlite Firefox extension and open de Bayer.db file. The results table can be exported to any CSV, TXT format.

Quickway:
Run the Bayer software on a Windows machine and copy the Bayer.db file to your linux machine for analysis.

---

### Post by Kaapeli64 on 2011-06-24
It seems that quite many people have been trying to get this glucose meter working on linux with no success. I've had some success in making things a little better :)

I did some investigating with an USB analyzer to find out what are the messages that are being sent to the device when the software reads the meter in windows. It turns out it is quite simple to replicate the message sequence from Linux and make the meter dump the readings out. I wrote a simple C program that does all that.

The sources are available on a git tree:

git://itanic.dy.fi/glucose

[http://git.itanic.dy.fi/?p=glucose;a=summary](http://git.itanic.dy.fi/?p=glucose;a=summary)

If you want to give it a try, remember that I really have no any idea what those messages does. It works for my meter, but I cannot guarantee it works for you. So you TRY IT AT YOUR OWN RISK. But if you want to give it a try, this is how you can clone and compile the sources:

```

# if you haven't ever compiled anything or you don't have git installed, you need to install the 
# necessary packages first

sudo apt-get install git-core build-essential

# First, clone the tree with git

git clone git://itanic.dy.fi/glucose

# Compile it

cd glucose

make

# and you're ready to run it:

./glucose

# Plug in your meter and it should dump the readings out


```Have fun!

---

### Post by mikewrichards on 2011-09-08
> **Kaapeli64 said:**
> ...
I wrote a simple C program that does all that.
...


Thank you thank you THANK YOU!  :D

Works like a charm!

---

### Post by Kaapeli64 on 2011-09-09
> **mikewrichards said:**
> Thank you thank you THANK YOU!  :D

Works like a charm!

Wow, cool. You are the first one I've heard to try out my tool :D It's nice to hear that it works for you too. Thanks for letting me know! :)

---

### Post by Jouke74 on 2011-09-09
Yes, thank you, it is working! 

It might require "sudo glucose" as I got permission denied accessing /dev/usb/hiddev0. Small access rights issue.

So great.

:guitar:

---

### Post by Kaapeli64 on 2011-09-10
> **Jouke74 said:**
> 
It might require "sudo glucose" as I got permission denied accessing /dev/usb/hiddev0. Small access rights issue.


Yes, indeed. I forgot about that. That's why I have this kind of udev rule in /etc/udev/rules.d/99-my.rules:

```

KERNEL=="hiddev*", MODE="0666", NAME="usb/%k"

```This will give rw-access to everyone for all hid devices and you will be able to run the reading SW with user permissions. It would be possible to make a rule that would give only specific group access to only the Contour device.. or such. But that works for me :)

---

### Post by Kaapeli64 on 2011-09-12
Just out of curiosity, have you got any ideas on how to process the data read from the meter? I have some scripts that I use my self, such as this:

```

#!/bin/bash

awk -F '|' '{ t = $7; if (t == "") t = "-"; print $9 "\t" t "\t" $4 }' | sed -e "s,\([0-9][0-9][0-9][0-9]\)\([0-9][0-9]\)\([0-9][0-9]\)\([0-9][0-9]\)\([0-9][0-9]\),\1.\2.\3\t\4:\5," -e "s,\.\.[0-9,A-F][0-9,A-F]\.\.,,"

```

Which will make the output a little more human readable. The rest of the scripts I have are not very generic. I have for example something that puts the fasting glucose graphs and basal insulin levels in the same graph. Then I have one graph for showing the daily averages and all results in one big graph.

Maybe I could extract some other useful information out of the readings as well, but I have somehow lost interest as I felt those graphs I have are sufficient.. More ideas are welcome :)

---

### Post by pyemus on 2013-03-23
Hi everyone,
I know it's been a while since last activity in this thread. But I wanted to ask if anybody tried experimenting with the contour USB device?
I tried to run Kaapeli64's glucose code on the contour USB, but it hangs in the 'initialize...' phase, and i cant seem to figure out where this goes wrong, anybody got an idea??

---

### Post by oldos2er on 2013-03-23
Old thread closed.

---

