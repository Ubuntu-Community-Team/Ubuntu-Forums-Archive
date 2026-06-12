---
title: "Hierowords 3.4.7 can't find a supporting file when starting up"
date: 2009-07-02
forum: General Help
---

### Post by 7Lj3)(P38J on 2009-07-02
Folks,

I run Karmic Koala, bu this problem began to occur with Jaunty as well.

I have installed a Windows-based hieroglyphic dictionary: Hierowords 3.4.7, running on Wine platform  (found at [http://home.comcast.net/~thot/index.html]("http://home.comcast.net/%7Ethot/index.html")).

In the beginning everything was fine, now it doesn't start up because it says the file "BasicList.CSV" was not found.

However, this file is correctly put along with all the other installation files in the folder /home/.wine/[c: drive or something like that]/Programs/Hierowords.

I tried moving the BasicList.csv file from place to place, but the application Hierowords still gives the same error and doesn't start up as it did previously.

I wonder if someone out there can help me ?

thanks
Carlos

---

### Post by 7Lj3)(P38J on 2010-11-14
SOLUTION FOR RUNNING HIEROWORDS UNDER LINUX - Copy/Paste from HieroWords website

Hierowords is written in Microsoft Visual Basic 6 for Windows. I get often asked if a version for Linux exists. Though strictly speaking it doesn't, I am told by Stan, a Linux Guru,  that it is possible to run Hierowords under Linux thanks to a platform called Wine (I do not use Linux, so I rely on what I am told).

Following are instructions that Stan Thomas sent me. I copied them here for your convenience.

Thank you Stan for finding this solution!

_______________________________________________________________________________

 

For Ubuntu Linux running Wine I followed the same instructions as for Windows.

You need wine installed. That should be as easy as typing:

sudo apt-get install wine

Then I downloaded the fonts and put them in my Wine fonts directory.

~/.wine/drive_c/windows/fonts/

To get the VB6 files (Msvbvm60.dll) I used winetricks.

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
chmod +x winetricks
sudo mv winetricks /usr/bin/winetricks
winetricks

Winetricks pops up a window where I selected which Windows package I needed installed. I selected vb6run.

Finally, I needed COMDLG32.OCX
I found a copy here:

[http://www.ascentive.com/support/new/images/lib/COMDLG32.OCX](http://www.ascentive.com/support/new/images/lib/COMDLG32.OCX)

I downloaded it and moved it to my Wine system32 directory.

~/.wine/drive_c/windows/system32/

Now I can run HIerowords on my Ubuntu Linux computer by typing  "wine Hierowords\ 346.exe"

It works great!

   -Stan

---

