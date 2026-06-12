---
title: "Grub problem - burg"
date: 2010-12-20
forum: General Help
---

### Post by YaegerBomb on 2010-12-20
So I attempted to install burg on my linux partition earlier and it completely screwed up.

Whenever I boot my machine I get sent to the grub prompt menu.

I need to fix this as I cannot use my machine (unless I boot from a USB). I have tried several solutions like reinstalling grub on the partition using the terminal (while on my USB Boot) but I get a type of embedding error (I can be more specific if necessary but to summarize i tried sudo grub-install --root... and the rest onto the correct partition and I get an error).

So now I am at a standstill. At the grub prompt I have tried:
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
set
ls /boot

but after this part I am not sure what to do. This was following someone that seemed to have the same problem but anything after that I am at lost.

My situation right now is that I have no access to a Ubnutu live cd. Nor a possible way to burn one for the next couple of days. Is there anyway to solve this problem from my usb boot or am I stuck right now?

Any help is great appreciated.

(NOTE I am not a common linux user, I usually only use my ubuntu partition for a quick boot or to remotely login to other machines and such so I am not entirely comfortable with the terminal (but trying to learn) so a n00b friendly guide of fixing would be nice.)

---

### Post by dcstar on 2010-12-20
> **YaegerBomb said:**
> So I attempted to install burg on my linux partition earlier and it completely screwed up.
.......

```
sudo dpkg-reconfigure burg-pc
```

Select the correct hard disk to install it.

---

### Post by YaegerBomb on 2010-12-20
> **dcstar said:**
> ```
sudo dpkg-reconfigure burg-pc
```

Select the correct hard disk to install it.

Okay not quite sure what I am suppose to do after I run this. Took me ages to figure out how to do it to begin with but now I am prompted with this:

"The following linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB legacy's menu.lst. Please verify that it is correct, and modify it if necessary."

Linux command line:
***BLINKING CURSOR WHERE I HAVE NO IDEA WHAT TO DO***

            <ok>

No idea what to do here so I hit okay.

brings me to another message

"The following string will be used as Linux parameters for default menu entry but not for recovery mode."

Linux default command line:

quiet splash *YAY ANOTHER BLINKING CURSOR*

       <ok>

so I hit okay as I have no idea what to do next.

Any suggestions? I have a live cd and tried running rescue and such but no luck. Not quite sure what ubuntu help page is talking about when it says you can select "Rescue broke system" or whatever because that option is not available AT ALL. I have tried typing Rescue into a prompt that I get to pop up and that just freezes at a certain point and sits there. 

Any help would be nice. It isn't nice to be without a fully functional laptop...

---

### Post by jonarnett90@gmail.com on 2012-01-02
I know I'm about a year too late, but did you run the "sudo burg-install "(hd0)"" command? I just installed burg and got the same messages during install. Outside of burg deciding to scare me by throwing out blah blah FAILED blah, it works pretty well.

---

