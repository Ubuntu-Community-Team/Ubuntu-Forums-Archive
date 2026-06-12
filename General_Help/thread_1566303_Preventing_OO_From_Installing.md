---
title: "Preventing OO From Installing"
date: 2010-09-02
forum: General Help
---

### Post by Agent69 on 2010-09-02
I have finally gotten around to installing Ubuntu 10.4, and I really like it, but it does irk me that OpenOffice is installed by default. Is it possible to prevent OpenOffice from being installed?

---

### Post by TBABill on 2010-09-02
No. It is part of the default installation. But you can go right into Synaptic, search for OpenOffice, then mark it for removal and click apply.

---

### Post by dcstar on 2010-09-02
> **Agent69 said:**
> I have finally gotten around to installing Ubuntu 10.4, and I really like it, but it does irk me that OpenOffice is installed by default. Is it possible to prevent OpenOffice from being installed?

OpenOffice is part of the default install, if you want to be picky install the Ubuntu Server CD and then manually install each desktop package you want.

---

### Post by arubislander on 2010-09-02
I'd think installing the lot and removing the little that is not wanted is much quicker than installing very little and adding the lot that ís wanted.

---

### Post by t0p on 2010-09-02
As the other posters have said/implied, I don't think there is a way to prevent Open Office from being installed (except by installing the server version, which will then entail installing a GUI and lots of other things you'll need day-to-day).

Much easier to just do the default installation, which includes Open Office, then remove the software you don't want.

Like you, I don't like Open Office.  AbiWord and Gnumeric meet my needs just fine.  But it really is a quick and painless procedure to remove unwanted packages and replace with apps you actually want.  Open Office is a popular app, whether you and I agree or not.  Can you imagine how many complaints there'd be if a key app like Open Office wasn't included and its fans had to install it themselves?  It would be terrible.  Much easier for the devs to include it by default and let us (the minority) remove it ourselves.

---

### Post by scouser73 on 2010-09-02
As stated in previous replies, there is no way to stop OpenOffice from installing but to remove the package once you've done an installation of Ubuntu.

**1** - Go to **Accessories** [COLOR="Red"]**>**[/COLOR] **Terminal**

**2** - Copy & paste this command to completely remove OpenOffice: > **sudo apt-get remove openoffice*.***

---

### Post by gypsumwolf on 2010-09-02
**->** You can download the Ubuntu ISO and use UCK (*Ubuntu Customization Kit*) with the ISO to remove any unwanted programs and then burn your new ISO to CD. Then you can install it every time how you want it.

**->** Or, if you want to take the time to individually select everything I recommend using the Minimal CD here: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

**->** And, another option is, you can write a BASH script to run every-time you install the Ubuntu ISO to remove your list of unwanted programs.

---

### Post by Agent69 on 2010-09-02
Thank you to everyone who responded. I appreciate your replies.

---

