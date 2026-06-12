---
title: "Install Brother MFC 7340 on Ubuntu 9.10"
date: 2010-04-22
forum: General Help
---

### Post by mdgrech on 2010-04-22
I managed to successfully install the Brother MFC 7340 on my Ubuntu box. I came across many discouraging posts on the forums and blogs stating that the printer was not compatible w/ Ubuntu. I'm here to tell you otherwise. Alright now lets get started...

```
sudo aa-complain cupsd
```

```
sudo mkdir /usr/share/cups/model
```

```
mkdir /var/spool/lpd
```

```
sudo apt-get install sane-utils
```

```
sudo apt-get install psutils
```

Download and install the deb [LPR driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brmfc7420lpr-2.0.1-1.i386.deb&lang=English_lpr") from the brother website

Restart cups ```
sudo /etc/init.d/cups restart
``` & connect your printer.

Navigate to [http://localhost:631/admin]("http://localhost:631/admin") in your web browser. Selecte Add printer. Select Brother MFC 7340 from list. Enter the human readable name for your printer. In the next screen the 7340 is missing from the list so select 'another make/manufacture' Select the MFC 7340 from the list and add printer.

Your install should now be complete, go ahead and print a test page.

---

### Post by raywood on 2010-05-13
This worked for me.  Thanks!

I've written this up in more detail and have included a bit about making the printer work in a VMware Workstation virtual machine running Windows XP.  See [http://raywoodcockslatest.blogspot.com/2010/05/installing-brother-mfc-7340-printer-in.html]("http://raywoodcockslatest.blogspot.com/2010/05/installing-brother-mfc-7340-printer-in.html")

---

### Post by dakkar9999 on 2010-05-13
Thanks!

---

### Post by mdgrech on 2010-05-13
Awesome! I'm glad I could help others out :)

---

### Post by quiricada on 2010-10-22
thanks, it works.

---

### Post by benf101 on 2012-01-31
The instructions on this thread didn't work for me.  This is what I did instead that did work: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

In a nutshell:

1. download the LPR driver ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html))
2. Open terminal
3. Navigate terminal to location of LPR driver that you downloaded in step 1
4. In terminal, type: sudo dpkg  -i  --force-all brmfc7340lpr-2.0.2-1.i386.deb
(YOUR FILE NAME MAY DIFFER IF YOUR MODEL IS DIFFERENT)
5. In terminal, type: sudo dpkg  -i  --force-all cupswrapperMFC7340-2.0.2-1.i386.deb
(AGAIN, FILE NAME MAY DIFFER)
6. Make sure it's installed.  In terminal type: dpkg  -l  |  grep  Brother

Go to that link for instructions on how to test out the connection.

---

### Post by oldos2er on 2012-01-31
Closed, necromancy.

---

