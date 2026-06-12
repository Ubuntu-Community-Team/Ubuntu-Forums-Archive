---
title: "Newbie is troubled by wireless keyboard"
date: 2010-05-14
forum: General Help
---

### Post by netnode on 2010-05-14
I decided to use the latest version of Ubuntu, 10.4 I think it is?

I installed it and my Logitech De Novo Edge wireless keyboard is not recognized and will not work! 

I need to get this keyboard working or I will have to revert to win7.

Is there any secrets I need to know.

I have no idea what I am doing, please help an old bloke.

---

### Post by cariboo on 2010-05-14
Could please plug in a ps/2 keyboard so that we can do some troubleshooting. Once you are a the desktop, could you open a terminal and type:

```
dmesg | tail -n15
```

just after you plug in the the remote sensor, paste the results in your next post. The above command will tell us if the remote sensor is detected properly.

Please don't threaten to go back to Windows, it just shows that you aren't really committed to giving a Linux variant a good try.

---

### Post by netnode on 2010-05-15
HI and thanks for the help.

After doing what you said I get this:

neil@neil-desktop:~$ dmesg | tail -n1
[ 3461.160071] usb 2-1: reset high speed USB device using ehci_hcd and address 2
neil@neil-desktop:~$ ^C


I did find blog about my problem, however, I don't even know how to get to the file:

/lib/udev/rules.d/70-hid2hci.rules

Link to the blog:

[http://awesomelinux.blogspot.com/2010/05/ubuntu-1004-lucid-logitech-dinovo-edge.html](http://awesomelinux.blogspot.com/2010/05/ubuntu-1004-lucid-logitech-dinovo-edge.html)

I did use the search file function and it failed to find /lib/udev/rules.d/70-hid2hci.rules

If this is the answer to fix it, can you please tell me how to access and change the file?

It's not a really good feeling to read so much good stuff about Ubuntu and then find it won't support a simple wireless keyboard.

I hope I can get this sorted as I am excited about using Ubuntu over windows.  :guitar:

EDIT:  When I do a bluetooth search it finds the keyboard, however, Ubuntu wants me to enter a pin into the keyboard?  Is that possible?

EDIT AGAIN:  I have managed to locate the file /lib/udev/rules.d/70-hid2hci.rules BUT it's protected and I can't edit it??

FINAL EDIT:

Don't Ask me how, but it's working wow!

---

### Post by netnode on 2010-05-15
forget it

---

