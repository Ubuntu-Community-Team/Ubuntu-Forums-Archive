---
title: "Lexmark Z32 killed by dapper drake"
date: 2006-06-07
forum: General Help
---

### Post by terminatorkobold on 2006-06-07
Hello everybody,

With my Dell computer i received a Lexmark Z32 printer for free. After having installed Ubuntu breezy, I constated with pleasure that the printer was easily installed with the ''install printer'' tool and worked nicely.

However since I upgraded to dapper drake my printer stopped working. I tried to delete it and reinstall, to no avail. Afterwards I tried to install the drivers from the Lexmark internet site using alien and dpkg but it failed. :( 

When I try to print a file it goes in the printing queue and simply sits there indefinitely. I get no error message and the file has the ''printing'' status forever n the queue. Has somebody an idea about the problem?

Thanks

---

### Post by givré on 2006-06-07
Try this howto, it's work wonderfully for me

 EDIT: wrong url, this one is ok
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by bluevoodoo1 on 2006-06-07
When I upgraded to Dapper it changed my Lexmark printer to a "network printer" instead of a "local printer."
Changing it back to "local" in system > administration > printing fixed my issue.

---

### Post by terminatorkobold on 2006-06-08
[QUOTE=bluevoodoo1]When I upgraded to Dapper it changed my Lexmark printer to a "network printer" instead of a "local printer."
Changing it back to "local" in system > administration > printing fixed my issue.[/QUOTE]

I constated the same thing, but configuring it to local did not help. Afterwards I even deleted the printer and reinstalled it to no avail. Finally I totally deinstalled cups from my system and reinstalled it, bu my problem remains. 

I don't understand what the problem is, the printer is detected without problem, meaning that the usb connxion is OK. Besides I get no error messge while printong. The file stays simply sitting in the queue. :(

---

### Post by givré on 2006-06-08
Read that [http://www.linuxprinting.org/pipermail/lexmark-list/2005q3/003194.html](http://www.linuxprinting.org/pipermail/lexmark-list/2005q3/003194.html)
and see if you have the same kind of problem. It's seems to effect all lexmark driver when use with alien

---

### Post by terminatorkobold on 2006-06-08
givré,

I tried the procedure in both of your links. It alloved me to install the printer with the z600 driver, but it did not help. I get exactly the same problem with the new driver.

It is funny, when I want to find the driver properties, the box is extremely slow to open. It was much faster with breezy, it is as if the program had problems to find something, but i don't know what.

my /var/log/cups/error_log is empty
and my /var/log/cups/access_log gives me the line
[INDENT]localhost - - [08/Jun/2006:16:48:42 +0200] "POST /printers/Z32 HTTP/1.1" 200 153831 - successful-ok[/INDENT]
when I install the printer and
[INDENT]localhost - - [08/Jun/2006:16:51:05 +0200] "POST / HTTP/1.1" 200 123 Get-Jobs successful-ok[/INDENT]
when I try to print something

---

### Post by givré on 2006-06-08
> the box is extremely slow to open.
It is also quite slow for me.
> It alloved me to install the printer with the z600 driver, but it did not help
You didn't really understand what i wanted to say. This howto is made for the z600 printer, but it should work for all driver provide by lexmark. You should install yours the way you want (with alian and dpkg if you want), and check that you don't have the permission problem pointed by the article i give you.

---

### Post by terminatorkobold on 2006-06-08
I just edited cupsd.conf to get more informations in the error_log file.

Now I get two error messages:

[INDENT]D [08/Jun/2006:17:32:50 +0200] CUPS-Get-Printers
D [08/Jun/2006:17:32:50 +0200] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [08/Jun/2006:17:32:53 +0200] cupsdReadClient: 5 POST / HTTP/1.1
D [08/Jun/2006:17:32:53 +0200] cupsdAuthorize: No authentication data provided.[/INDENT]

and

[INDENT]D [08/Jun/2006:17:32:54 +0200] [Job 74] LPGETSTATUS returned a port status of 10...
W [08/Jun/2006:17:32:54 +0200] [Job 74] Printer fault![/INDENT]

Any ideas

---

### Post by terminatorkobold on 2006-06-08
[QUOTE=givré]
You didn't really understand what i wanted to say. This howto is made for the z600 printer, but it should work for all driver provide by lexmark. You should install yours the way you want (with alian and dpkg if you want), and check that you don't have the permission problem pointed by the article i give you.[/QUOTE]

I tried to use the lexmark z32 driver, but the package provided by Lexmark for the Z32 printer doesn't include a cups ppd files, in contrary to the z600 package. I was therefore unable to use the given instructions with the z32 driver that I downloaded from the lexmark internet page.

---

### Post by terminatorkobold on 2006-06-09
Lastly I tried to configure  cups using the web interface:  [http://localhost:631](http://localhost:631)

However in order to change a configuration, the interface asks me my username and password. After i type them I get a permission denied answer. I wonder if all my problems come from sudo rather than cups.

I think I'll file a bug report about it.
Somebody has another idea?

---

### Post by Hairy_Palms on 2006-06-09
hmmm all i can think is it meight be an upgrade problem, i dont have your exact model but ive got 2 lexmarks a Z22 and a Z25 they both work fine on a fresh install of dapper

---

### Post by wsscott on 2006-06-09
I have the exact same problem w/ a lexmark Z53.  It's a fresh install of Ubuntu 6.06.  The printer worked fine under Breezy.  The printer spits out paper w/ nothing printed.

---

### Post by Mickeysofine1972 on 2006-06-09
[-o< I have the exact same problem!

In Breezy I used to fix it with this:

sudo chmod 777 /dev/usb/lp0

This worked fine but now I've upgraded there is no /dev/usb/lp0 ! I only have /dev/usblp0 and the chmod doesn't work on that either!

Mike

---

### Post by Mickeysofine1972 on 2006-06-13
Hi 

just so other can know.....

I got my z32 working by scrapping the usb cable and connecting it via parallel port!

There is some crash permissions thing going on with CUPS and /dev/usblp0 that doesn't happen when you use the parallel port instead!

Mike

---

### Post by terminatorkobold on 2006-06-13
[QUOTE=Mickeysofine1972]Hi 

just so other can know.....

I got my z32 working by scrapping the usb cable and connecting it via parallel port!

There is some crash permissions thing going on with CUPS and /dev/usblp0 that doesn't happen when you use the parallel port instead!

Mike[/QUOTE]

It is really weired. I tried to give the cups daemon root privilege by editing my sudoers file but it didnt't help.

Chmoding /dev/usblp0 did not work either. The command does nothing to the file, it looks as if its permissions cannot be changed.

---

### Post by Mickeysofine1972 on 2006-06-15
Hi 

Unfortunatley, the chmod thingy only works on Breezy so if you MUST have printing via a USB you could always downgrade! (yeah like thats an option!)

BTW the z32 has been working fine ever since! so a quick trip to the scrap yard to dig out an old parallel cable is work the trouble I think!

Mike

---

### Post by terminatorkobold on 2006-06-20
[QUOTE=Mickeysofine1972]Hi 

BTW the z32 has been working fine ever since! so a quick trip to the scrap yard to dig out an old parallel cable is work the trouble I think!

Mike[/QUOTE]

Hi Mike,

Replacing the usb cable with a parallel cable effectively solved my problem. However I already have a zip drive on the parallel port, so it is not a satisfactory solution. Ill go fill a bug report.

Thank you for your time! O:)

---

### Post by magnocrow on 2006-07-05
**Downloading driver from lexmark site and install

[http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz](http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz)

sudo tar -zxvf z32_eng_us-1.0-5.tgz
cd rpm/z32/english_US
sudo alien -c lexmarkz22-z32-1.0-5.i386.rpm
sudo dpkg -i lexmarkz22-z32_1.0-5_i386.deb

**Downloading and install lexmark-footmatik-kit

[http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz](http://www.linuxprinting.org/download/printing/lexmark-foomatic-kit.tar.gz)

sudo tar -zxvf lexmark-foomatic-kit.tar.gz
cd lexmark-foomatic-kit
sudo sh install
sudo pearl lexmarkinstall

...

***Edit ppd file in /etc/cups/ppd

sudo gedit ppdfile.ppd

edit file and change instances of /dev/usb/lp0 , /dev/usb/lp1, /dev/usb/lp2 change to /dev/usblp0, /dev/usblp1,/dev/usblp2.

***Add user in printer group

sudo adduser <username> lp

***Add alias in your ~/.bashrc to run the align and clean pages,  new commands  printalign and printclean for lexmark printer.

sudo gedit ~/.bashrc

add lines in end of file

alias printclean='cat /usr/local/lexmark/z32/lxaecln.out > /dev/usblp0'
alias printalign='cat /usr/local/lexmark/z32/lxaealgn.out > /dev/usblp0'

save the file.

reboot your PC

and use you printer :lol:

---

### Post by terminatorkobold on 2006-07-07
Hi magnocrow,

You are a genius, it worked like a charm! I am happily printing everything that I want. :-D :-D 

Thank you so much for your time, if I can ever do something for you, tell me!

---

