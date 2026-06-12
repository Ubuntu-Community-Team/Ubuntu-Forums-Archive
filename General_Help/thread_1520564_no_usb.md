---
title: "no usb?"
date: 2010-06-29
forum: General Help
---

### Post by udornf4 on 2010-06-29
Just installed 10.04. Inserted a flash drive into the usb port. Nothing?

How do I tell if the usb ports were installed by ubuntu?

---

### Post by supergrav on 2010-06-29
try lsusb in command line to see if your drive is recognised.

---

### Post by davidmohammed on 2010-06-29
before you insert the usb device type in a terminal

lsusb

dmesg

then add the usb device.

type

lsusb

dmesg

your device should then be displayed by lsusb
dmesg will show how the system recognised the usb device and if there was any errors

copy and paste the results here (in code tags) if you need further help.

---

### Post by udornf4 on 2010-06-29
> **davidmohammed said:**
> before you insert the usb device type in a terminal

lsusb

dmesg

then add the usb device.

type

lsusb

dmesg

your device should then be displayed by lsusb
dmesg will show how the system recognised the usb device and if there was any errors


copy and paste the results here (in code tags) if you need further help.

====================================================

Thanks for the help.

Don't know what is meant by: "before you insert the usb device **type in a terminal**"?

And, I am not familiar with the **term**: **" (in code tags)"**

---

### Post by davidmohammed on 2010-06-30
choose Accessories - Terminal.

type what I said.

copy the text

reply to this message

click the # in the message menu options (third button from right on the line B I U etc)

it will add CODE /CODE  in square brackets...

paste the text copied between the code-tags (square brackets)

---

### Post by udornf4 on 2010-07-05
OK, a little late in reply (relatives on the 4th)...

Followed your directions thru the dmesg and the USB device was found, etc. But then what? I couldn't find the actual usb device anywhere.

I don't understand "click the # in the message menu options (third button from the right on the line B I U etc)"

Where is "message menu options" - couldn't find that... (or third button from the right on the line B I U...)

Sorry for my ignorance...

---

### Post by silverbirch on 2010-07-05
i jsut had a problem with the flash drive not seen.

try this from menu        system / administration / disk utility

you may see the usb there 

i formatted from there and the PC sees the device now in the home folder

but you may have data on it , so perhaps not an option for you

all the best ;)

---

### Post by davidmohammed on 2010-07-05
> **udornf4 said:**
> OK, a little late in reply (relatives on the 4th)...

Followed your directions thru the dmesg and the USB device was found, etc. But then what? I couldn't find the actual usb device anywhere.

I don't understand "click the # in the message menu options (third button from the right on the line B I U etc)"

Where is "message menu options" - couldn't find that... (or third button from the right on the line B I U...)

Sorry for my ignorance...

[IMG]http://dl.dropbox.com/u/3575524/codetag[/IMG]

---

### Post by udornf4 on 2010-07-05
David - you are a patient person! I understand from your picture - no problem. 

But WHERE does this menu come from? When I go to Application - Terminal - there is no such menu.

---

### Post by davidmohammed on 2010-07-05
you've started your terminal through the menu option

Accessories - Terminal
correct?

then you typed

 lsusb

correct?

This displayed a bunch of text.
Highlight all of the text - right click and select copy

Now reply to this post - you will see the above menu on your reply options

click that # button.

put your cursor between the code /code text
right click and click paste.

Repeat the above but with
dmesg
in your terminal.

---

### Post by Crazedpsyc on 2010-07-05
if your talking about the CODE block still, the # button is not in an application, it is in the reply toolbar (right here in the forums) click the "New Reply" button right below the last post or above the first one.
it is not Application>Terminal, it is Applications>Accessories>Terminal.
it will open up displaying a prompt similar to youser@host-laptop or @host-desktop or something. type in
```

lsusb

```
and hit enter.
a bunch of text will appear.
select it with the cursor and hit Ctrl+****+C to copy it.
post it on here in CODE tags (the # button) and it will look just like that spot up there where it says "lsusb"
do the same with "dmesg".
also try right clicking on the bar at the top or bottom of your screen (doesn't matter which) and click "Add to Panel"
then search through the list to find "Disk Mounter"
select it and click the add button. in the spot you right  clicked there should be an icon.
click the icon and select Mount blahblah
then look on your desktop for the thumb icon and double-click it.

---

### Post by udornf4 on 2010-07-05
OK, All I can say is DUH!

I fully understand, now. Thanks to both you guys!

Will post my results soon...:)

---

### Post by udornf4 on 2010-07-06
OK, up and running... Thanks to all!!!:KS

---

