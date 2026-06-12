---
title: "firefox stopped downloading"
date: 2010-03-27
forum: General Help
---

### Post by ubunterooster on 2010-03-27
I was trying to get e-sword and wine from the respective sites and firefox suddenly stopped allowing downloads.

---

### Post by Tom.Lane on 2010-03-27
Hello.

Please provide more information about this issue.


[LIST]
[*]What exactly happened?
[*]What were you running at the time?
[*]What version of firefox are you running?
[/LIST]

Tom

---

### Post by ubunterooster on 2010-03-27
What happened: I was downloading Wine from its site; it downloaded.Then I tried to download e-sword from its site. It did not work so I tried redownloading wine with no succsses. 
What was running: firefox with three tabs (ubuntu forums, wine's site, and e-swords site
What version: 3.5.8

---

### Post by ubunterooster on 2010-03-27
>  Downloading Temporarily Unavailable

The server is temporarily unable to service your request. If you are currently downloading another file, then be patient and wait for that download to complete before beginning another.

If you are unable to download any files, then possible problems you may need to correct include:

    * Disable any download manager you might be using and see if that helps.
    * Do not use the MSN browser, try Internet Explorer or Firefox instead.
    * Sometimes a firewall prevents the downloading of files.

Click here to go back and try again. 
	
^this is the error message that I got

---

### Post by tkoco on 2010-03-27
> **ubunterooster said:**
> ^this is the error message that I got

May be your that ISP DNS server is the culprit. Try changing the DNS servers to point to the Google Open DNS servers, 8.8.8.8 & 8.8.4.4  and see if that helps with your problem.

---

### Post by ubunterooster on 2010-03-27
EDIT: trying....

---

### Post by ubunterooster on 2010-03-27
Nope, still does not download :(

---

### Post by tkoco on 2010-03-27
> **ubunterooster said:**
> How? (epiphany-browser also stopped downloading, so I think you are correct)
EDIT: That Pc is not letting me edit posts so I am at another

I had a similar situation and I traced the connection problem to the ISP DNS. Try it. Nothing ventured, nothing gained. It won't make things any worse than it is currently.

---

### Post by Enigmapond on 2010-03-27
Forgive me but I'm a little confused. Why are you trying to install Wine from the site instead of going though the PPA? [https://launchpad.net/~ubuntu-wine/+archive/ppa ]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

Also do you have another browser, possibly Chrome, that you could try to download e-sword on? Just to see if it's actually FF or your ISP.

---

### Post by ubunterooster on 2010-03-27
> **Enigmapond said:**
> Forgive me but I'm a little confused. Why are you trying to install Wine from the site instead of going though the PPA? [https://launchpad.net/~ubuntu-wine/+archive/ppa ]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

Also do you have another browser, possibly Chrome, that you could try to download e-sword on? Just to see if it's actually FF or your ISP.

Tried Epiphany, no difference. (Desktop in other room is fine, BTW) And I did do the PPA. Also changed ISP DNS

---

### Post by Enigmapond on 2010-03-27
I just downloaded the install.exe for e-sword with no problem...if that's what you were trying to do, I have no answer for why you weren't able to....heh...you want it?..:)

---

### Post by ubunterooster on 2010-03-27
Actually, no; I used wget to get it. The problem is I am not the main user of the computer and I can't tell my father to wget every .pdf document

---

### Post by ubunterooster on 2010-03-27
Reinstalling Karmic :( ...... This BETTER work

---

### Post by ubunterooster on 2010-03-27
I reinstalled and it did not work. The problem is the firewall. So until I figure it out ufw needs to stay off (it's within our networks firewall so all SHOULD be okay)

---

