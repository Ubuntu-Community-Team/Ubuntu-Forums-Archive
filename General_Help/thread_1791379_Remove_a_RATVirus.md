---
title: "Remove a RAT/Virus?"
date: 2011-06-26
forum: General Help
---

### Post by Flotonic on 2011-06-26
Odd things have been happening. My Internet slows down a whole lot at times, my YouTube Account says I "Liked" a video at a time I wasn't even using the computer, and probably some other stuff I still haven't caught yet. I even had a fully functional program saved that was about one hundred lines. When I opened it today, I see this (a malformatted "Hello World" program):
```
#include <stdio.h>
int main(){printf(Hello,world!n);return 0;}
```It seems like it's a RAT or some other kind of virus. Does anyone have any tips for removing such a pest? Thanks in advance!

---

### Post by terrykiwi83 on 2011-06-26
have you tried installing ClamAV and running it?

---

### Post by coldraven on 2011-06-26
If you are using wi-fi I would change the key and check your encryption settings. It should be WPA.
I log into my router with [http://192.168.2.1/](http://192.168.2.1/) in Firefox, that is where you need check.

---

### Post by Dangertux on 2011-06-26
Interesting. 

Could you post the output of netstat -a

You could also check out rkhunter

---

### Post by Flotonic on 2011-06-26
Thanks for the support.

Here are the netstat -a results: [http://pastebin.com/g7Utdfnf](http://pastebin.com/g7Utdfnf)

I tried KlamAV. It seemed to go for infinity and, when it picked up the same file twice, I decided that it's time to stop the scanning.

The only things that it picked up were the following:
WINXPPROX64.BAT    Trojan.Agent-26117
(And an HTML page I downloaded. It said HTML.Phishing.Auction-18. I know it's harmless for a fact.)

WINXPPROX64.BAT was from when I was trying to burn a Windows XP disk forever ago, and the problems didn't start happening until recently. I selected "Quarantine," anyway.

The problems weren't happening until I downloaded and tested something that someone sent me. I've deleted the program since, but perhaps it somehow installed something or spread or something.

What is the best thing I could possibly do in this situation?

---

### Post by sam_delta on 2011-06-26
Personally i would grab important files from my home, and do a reinstall. There might be something else, but it can be time consuming and you might end up without removing it completely.

Did you ran the program as 'root' (with sudo)? which was the program you ran?

sam

---

### Post by Flotonic on 2011-06-26
I ran the program not with sudo, but by typing the fully directory to the program from Terminal and pressing Enter. I also tried double clicking.

I can't really share the program name because it wasn't from an official distributor, so others don't have anything to worry about.

---

### Post by Dangertux on 2011-06-26
I highly recommend the following -- 

Get chkrootkit 

sudo apt-get  install chkrootkit 
sudo chkrootkit

and rkhunter
sudo apt-get install rkhunter 
sudo rkhunter --check

They likely will not find anything, however watch closely if they note any odd issues with file permissions or files that are "suspicious" 

Failing this, consult the PM I sent you. Also if none of the options you have are satisfactory, a reinstall may be in order.

---

### Post by antaios256 on 2011-06-26
this is really interesting i have no idea what could cause that it almost sounds like a rootkit was installed and opened a back door. i would be interested in seeing what you find in yoru search for your cause.

---

### Post by Thewhistlingwind on 2011-06-26
Indeed. If you find any malicious executables, be sure to pass them on. 

Unless you can't, of course.;)

---

