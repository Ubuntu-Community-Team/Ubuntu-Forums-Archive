---
title: "Hopefully dumb question re: SSH &amp; printing"
date: 2011-06-30
forum: General Help
---

### Post by bpb_21 on 2011-06-30
I've been researching this for a while and I've arrived at hopefully what is a dumb question that will solve my issue.

I'm running Ubuntu Server 11.04 on one computer, with the only remote access (either LAN or WAN) available via SSH RSA keys (no password sign-in allowed).  It's primarily set up to store Deja Dup backups from my main "production" laptop, running the regular desktop Ubuntu 11.04.

I'd also like to host an HP Officejet 5610 MFD on the server, from the command line, no GUI involved.  That removes the web interface of [http://localhost:631](http://localhost:631) on the server, which the HP is connected to.

I've gotten as far as enabling the laptop to see the HP printer on the sever and send (or attempt to send) print jobs to it, but unsuccessfully.

Question: is SSH sufficient to handle print jobs?  Or do I need to enable another protocol/service as well to actually scan and print?  (Cups is running on client and server.)  If so, does this decrease the security of the SSH connection?

---

### Post by Cheesehead on 2011-06-30
CUPS robust command-line tools, so you don't really need the web interface. 
Also, CUPS' web interface is not related to whether there's a GUI installed on the server - your laptop browser can access the server CUPS page, too. 

Here is how I troubleshoot these, in order:
1) Is the server firewall be blocking port 631, preventing CUPS from communicating?
2) Is CUPS on the server working? Can you print a test page on the server from the command line?
3) Is CUPS on the server configured to share printers?
4) Is CUPS on the laptop working? Is CUPS on the laptop configured to listen for shared printers? Is an old printer config (usually with the same name) sitting on the laptop, overruling the share? 
5) Try to print a laptop document to a server-shared printer. Does the shared printer show up in printing dialogs?

---

### Post by bpb_21 on 2011-06-30
Thanks for the tips; I'm going to try those when I get back to the server machine.  That should give me some direction with this.

---

### Post by bpb_21 on 2011-07-01
> **Cheesehead said:**
> CUPS robust command-line tools, so you don't really need the web interface. ...
Here is how I troubleshoot these, in order:
1) Is the server firewall be blocking port 631, preventing CUPS from communicating?
2) Is CUPS on the server working? Can you print a test page on the server from the command line?
3) Is CUPS on the server configured to share printers?
4) Is CUPS on the laptop working? Is CUPS on the laptop configured to listen for shared printers? Is an old printer config (usually with the same name) sitting on the laptop, overruling the share? 
5) Try to print a laptop document to a server-shared printer. Does the shared printer show up in printing dialogs?

So...humor me and help a struggling newbie out?  I appreciate the steps, but I'm stuck on #2.  I don't know how to print a test page from the command line in the first place.  I tried "man cups" and got "No manual entry for cups" (perhaps I'm being incredibly dense) and tried the steps on these links below to no avail (been Google-ing the heck out of this with mostly nothing useful).  I know there are man pages for cupsd, and I've followed the "see also" links, but I keep going around in circles ending up at "use the web interface at http://localhost:631" and I don't have a web interface on the local host (my server).  Am I just looking for the wrong man pages?

[http://www.cups.org/doc-1.1/sam.html#4_2_1](http://www.cups.org/doc-1.1/sam.html#4_2_1)

[http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html](http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html)

[http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS](http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS) (steps adjusted since I'm not using Slackware distro)

I'm trying to do my homework on this!  Are there any resources out there on the cups command line?

---

### Post by bpb_21 on 2011-07-01
And here those resources are, and on the client too!  Maybe there's hope for me!
[http://localhost:631/help/options.html](http://localhost:631/help/options.html)

Ok, I take that back.  the page on command-line printing ([http://localhost:631/help/options.html?TOPIC=Getting+Started&QUERY=](http://localhost:631/help/options.html?TOPIC=Getting+Started&QUERY=)) says to use lp or lpr.  Those give

lp: Error - scheduler not responding!

and

The program 'lpr' can be found in the following packages:
 * cups-bsd
 * gnuspool
 * lpr
 * lprng
Ask your administrator to install one of them

error messages, respectively.  Installing lpr or gnuspool removes some/all of the cups-client (on the server machine; I'm trying to print anything at all from the command line).

IF I ever get this figured out I'm writing an uber-guide for newbies like myself on how to configure a printer, attached to a server, using Ubuntu.

---

### Post by bpb_21 on 2011-07-02
Ok in desperation I tried to completely remove cups client, server, all of it and then reinstall.  That didn't go so well.

So, it is impossible to configure a printer attached to a "headless" server in Ubuntu.

Back to Windows.

---

### Post by middlechild on 2011-07-04
[SIZE=3]It is not impossible to configure a printer using a headless server.  I have an HP 5500 working on a headless server for my home network of 5 computers.    There are more than one issue, and it takes some time but once it is configured it works.
[/SIZE]

---

### Post by bpb_21 on 2011-07-05
> **middlechild said:**
> [SIZE=3]It is not impossible to configure a printer using a headless server.  I have an HP 5500 working on a headless server for my home network of 5 computers.    There are more than one issue, and it takes some time but once it is configured it works.
[/SIZE]

Yeah, I know.  (Sigh.)  Configuring user profiles, SSH RSA key authentication, network drives, etc. all that turned out to be easy compared.  Who knew?  I can't even get CUPS installed back correctly - now it just hangs at "Setting up cups (1.4.6-5ubuntu1.2) ..." until I reboot.  When I do, and run dpkg to correct the partial install, it appears to work but I don't end up with a cupsd.conf file in /etc/cups/

I'm too hard headed to give up, so I guess I'll get it eventually, but talk about frustrating.

sudo dpkg --configure -a
sudo apt-get autoremove --purge cups
sudo apt-get install cups

Now cups is back and I'm at it again.  Maybe I will mark this thread genuinely solved sooner or later.

---

