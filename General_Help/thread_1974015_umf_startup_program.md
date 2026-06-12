---
title: "umf startup program"
date: 2012-05-05
forum: General Help
---

### Post by Areku The O.F. on 2012-05-05
Im using Precise on my PC, and suddenly out of nowhere this startup program is appearing among the rest. Since it offers no description of what it does I decided to delete it, only to have it appear again on the next startup. It may be something harmless as my PC works just fine but it kind of annoys me. If it helps I'm also using Precise on my Netbook and this startup program is nowhere to be seen. Thanks in advance!

Here's a picture
[http://img152.imageshack.us/img152/9131/umf.png](http://img152.imageshack.us/img152/9131/umf.png)

---

### Post by hal8000 on 2012-05-05
Do you have an Ubuntu Cloud account?

The only thing I could find on google was about UMF cloud pilot, but just a guess. I'm using a different linux at the moment, so will check next time I reboot into Precise, and see if its running on my system.

Programs can start from a number of locations, including the runlevels,
/etc/rc.local, .xinitrc and home ~/.xinitrc if you have a file. This list is not complete and there are other locations as well.

---

### Post by Cheesemill on 2012-05-05
If you select the umf entry and then click on 'Edit', what details does it give you about the application and what is the full path to the command it is calling?

---

### Post by Areku The O.F. on 2012-05-05
/home/areku/.config/autostart/dbus-session-addr-save.sh

It takes me there, and even If I delete it it comes back again.

---

### Post by Auslegung on 2012-05-23
Bump?

Is no one else seriously concerned about this?  I can find no information on the web.

---

### Post by grahampositive on 2012-08-09
I can confirm that I have the same startup program, which directs to the same path. The contents of this .sh file are as follows:

echo ${DBUS_SESSION_BUS_ADDRESS} > /tmp/.umf_[home]

where [home] is the name of my home folder. 

It seems that the program is outputting some text using the echo command into a file in the /tmp folder. The contents of that file are:

unix:abstract=/tmp/dbus-ARcrQ2DVyi,guid=fcf5586c38e81175d7623065000001a1

I have no idea what the purpose of this is, but it seems to be referring to another file in the /tmp directory, but I don't see anything there that looks like the output above. 

this is the ls output of my /tmp directory


8780752926C0B3F5D84A25450D45F7E9F3023036.18.0.1025.168_service_ipc
at-spi2
CRX_75DAF8CB7768
filet8RALl
keyring-HWscZu
orbit-grahamcl
pulse-2L9K88eMlGn7
pulse-PKdhtXMmr18n
pulse-UTGiGmFMW3vZ
sni-qt_vidalia_6630-h6KmHu
ssh-xDJOKMaI1957
tmpbEV8aC
unity_support_test.0


this is really weird and I'd certainly appreciate it if someone could tell me what this program is doing.

---

