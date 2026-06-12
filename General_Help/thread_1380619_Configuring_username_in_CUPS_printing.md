---
title: "Configuring username in CUPS printing"
date: 2010-01-13
forum: General Help
---

### Post by ecl7 on 2010-01-13
Hello,

My school uses the Pharos printing system, and they recently made a change in which we must print with our school ID.  However, my ubuntu username is not the same as my school ID, which means that even though I can set up the printer through CUPS, I cannot print using the correct ID.

The only solution I have seen is to make another account with my school ID, but I find it annoying to have to switch users every time I want to print.  I noticed in the CUPS options that there is a setting under "Job storage" that allows you to use a "Custom user name".  Does anyone know how to configure this?

Thanks!

---

### Post by Snow Pickles on 2010-09-10
I know that this is an old thread, but I've come up with a solution after hours of searching, and thought I should share it.

Go to system-config-printer (that's System > Administration > Printing )
Go to New > Printer (give it a bit)
Instead of entering a URI, go to Network Printer > LPD/LPR Host or Printer
You should see a text field for host and queue.

To specify a username, in the host field enter:

```
username@host
```In my case, at BYU Provo, I entered in the host field:
```
net_id@isis.byu.edu
``` and in the queue field:
```
CampusBW
``` 

The rest is straight forward.

One note though, I read that the same **should** be accomplished by using CUPS and entering in the URI:
```
lpd://username@host
```but the "username@" part gets deleted, and the only way to get this to work is to use the aforementioned method of making a new local account with the said username.
Even more interestingly, checking out /etc/cups/printers.conf revealed the settings for both the Gnome-setup and CUPS-setup printer were nearly identical, notably the line
```
DeviceURI lpd://net_id@isis.byu.edu/CampusBW
```Even though CUPS didn't show it, it still stored the username, but something still doesn't work.

---

