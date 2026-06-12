---
title: "Brother  scannner MFC-6490CW - not working after ubuntu upgrade to Natty 11.04"
date: 2011-05-27
forum: General Help
---

### Post by concite on 2011-05-27
I have a Brother MFC-6490CW network Scanner.  Had it installed and working great in Gutsy.  Upgraded to Natty 11.04 the other day, and the scanner stopped working.  Printing is still ok.  When I try to open a scanning program I get:

"No Devices Found"

Any thoughts?  I tried reinstalling the drivers, no luck.  Been trolling the forums, but nothing jumps out at me.

---

### Post by demonipuch on 2011-05-27
Hi

Did you install brscan3 available for your scanner on [Brother support website]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html")?

Here is an howto install and use a Brother scanner over your network :

1- Make sure sane-utils is installed :
```
sudo apt-get install sane-utils
```2- Download the right driver depending if you're using 32 bits or 64 bits system :
```
wget http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb
wget http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb
```3- Install the driver :
```
dpkg -i brscan3-0.2.11-4.i386.deb
dpkg -i brscan3-0.2.11-4.amd64.deb
```4- Add a network scanner entry :
```
brsaneconfig3 -a name=SCANNER model=MFC-6490CW ip=your_scanner_ip
```5- Confirm the network scanner entry :[FONT=monospace]
[/FONT]```
brsaneconfig3 -q | grep SCANNER
```You can skip step 2 and 3 if you have already installed the driver.

Hope it helped

edit :

If you're using your scanner via USB, you need to :

Open/Create the file /etc/udev/rules.d/40-libsane.rules
```
sudo nano /etc/udev/rules.d/40-libsane.rules
```Add this at the end of file :
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```Save and exit.

Restart your computer

---

### Post by concite on 2011-06-01
OK - got it fixed.  Had to uninstall all drivers and config then reinstall from scratch.

i.e.

```
brsaneconfig3 -r NAMEOFMYPRINTER
sudo dpkg -r brsane3
sudo dpkg -r brscan-skey
```

Then follow instructions in the post above and all worked.  Thanks for pointing me in the right direction

---

### Post by Rebelli0us on 2011-06-01
I have a Brother MFC that I'd love to use for scanning in Linux, but I have NO idea what the above instructions mean. Is Brother actually publishing Linux drivers for their hardware??

---

### Post by concite on 2011-06-01
They do - I have a network scanner up and running on linux.  It has been working great for a year or two until an Ubuntu upgrade broke it.  Uninstalled the drivers and reinstalled the drivers and it worked.

Go to:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

install the scanner driver, scan key tool and follow the driver installation instructions and you should be up and running.

---

### Post by liferules on 2012-04-21
For any other looking for a solution for scanner not found look on the Brothers site here: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

Basically, all I had to fix my issues on 11.10 64bit was to copy files and directories:

/usr/lib64/ to /usr/lib/

After months of trying to figure it out now it is fixed...

---

