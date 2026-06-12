---
title: "US Robotics usb modem firmware update"
date: 2010-10-26
forum: General Help
---

### Post by Silvertones on 2010-10-26
I need to update the firmware on this modem. I DL the file but don't understand the Read Me instructions.
They tell me to do this:

The attached zip file contains the following files:

modem_ei.hex > 1.2.19 modem firmware
ocmfldr.hex > Firmware loader
mdmflash > Compiled executable for 2.6.x kernels only.

Run the mdmflash file from a terminal prompt to update the modem firmware
Example: user@domain:~$ ./mdmflash

---

### Post by searchfgold6789 on 2010-10-26
[LIST=1]
[*]Copy the "mdmflash" file to your home directory.
[*]Open up the terminal, its under Accessories.
[*]At the window type in ```
sudo ~/mdmflash
```
[*]Type in your password which will not appear, then press enter.
[*]The installation will begin.
[/LIST]
Hope this post helped.
 - search

---

### Post by inameiname on 2010-10-26
Sounds like all you do is extract the zip file, and then open a terminal inside it's folder that was extracted (either directly or 'cd "/path/to/folder", and then inside the terminal again, enter the following, to run the 'mdmflash' file:

sudo ./mdmflash

---

### Post by Silvertones on 2010-10-26
Thanks. I'm familiar somewhat  with terminal. If I had looked closer I would have realized that this;
```
user@domain:~$
```Was already there in terminal all I needed to do is type in:
```
./mdmflash
```

Now how do you open terminal in the folder were the file is.

---

### Post by inameiname on 2010-10-26
You can open a terminal in the folder through several ways (here are three):

1. Installing nautilus-open-terminal is always a great idea, as it'll give you a simple right click choice to open a terminal in whatever window you are currently in (such as the folder with 'mdmflash') through nautilus:

You must install it first, by typing in the terminal:

sudo apt-get install nautilus-open-terminal && nautilus -q

2. Using a nautilus-script, such as the one below.

```

#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#        - Added checking if executed on Desktop "x-nautilus-desktop:///"
#          so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}

```3. Just 'cd-ing' into it. First open a terminal window, and then type:

cd /path/to/mdmflash

---

### Post by searchfgold6789 on 2010-10-26
Reply to post #4:
```
cd <path to where mdmflash is>
```

---

### Post by Silvertones on 2010-10-26
Thanks folks.
Nautilus-open-terminal is perfect but now I also know the other way as well.
So much to learn.

---

### Post by inameiname on 2010-10-26
Indeed. 

Oh, and for future use, here is a simple terminal command to make use of that Window's Key on your keyboard. If you copy and paste this into the terminal, it'll make it so every time you click that Window's Key on your keyboard, it'll open a terminal window. Makes it much easier to use it.

gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal --type string "Super_L"

---

