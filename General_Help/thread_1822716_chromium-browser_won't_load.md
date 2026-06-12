---
title: "chromium-browser won't load"
date: 2011-08-10
forum: General Help
---

### Post by brandon88tube on 2011-08-10
For a long time now, chromium-browser just opens and eventually throws the unresponsive error message up and asks me to kill the pages or wait. None of the options work, can't even get to the preferences because that is now a page inside the browser. I have purged, reinstalled, tried manually deleting the folders, installing Google Chrome, purging, reinstalling that with no luck. Unless, I missed a location where it is still storing something, I have absolutely no idea what the problem is. I wanted to know if anyone could help with this problem.

Edit: Forgot to mention, I'm running 10.04

---

### Post by Toz on 2011-08-11
The user-specific settings should be stored in ~/.config/chromium. Try moving/renaming the folder and see if that helps.

---

### Post by wojox on 2011-08-11
Also try opening it from the terminal. It will give you some good info there.

---

### Post by brandon88tube on 2011-08-12
Toz and wojox,

I've already done what both of you have suggested, but I decided to give it another go. Neither worked and when I run chromium-browser in the terminal, nothing outputs to the terminal. If there is a verbose command/flag to run it under that might help, but I don't know if it has one. I think many kernel updates ago, it broke something with chromium.

---

### Post by Toz on 2011-08-12
Here is a list of switches: [http://peter.sh/experiments/chromium-command-line-switches/]("http://peter.sh/experiments/chromium-command-line-switches/")

Anything being logged in ~/.xsession-errors?

There is also a ~/.cache/chromium folder you could move/delete.

---

### Post by brandon88tube on 2011-08-12
Already tried the cache folder, but I tried again anyways. I also checked the .xsession-errors and didn't seem to show anything chromium related... though did find some other stuff had some errors that I never paid attention to ;)

I might try some sort of debug mode option from that huge list of switches, but I'm very doubtful that this will help much.

I appreciate the help and please keep throwing ideas at me.

---

### Post by Toz on 2011-08-12
Interesting. On my computer, 11.04, /usr/bin/chromium-browser is a script that starts up the browser. The usage states:
> usage () {
  echo "$APPNAME [-h|--help] [-g|--debug] [--temp-profile] [options] [URL]"
  echo
  echo "        -g or --debug           Start within $GDB"
  echo "        -h or --help            This help screen"
  echo "        --temp-profile          Start with a new and temporary profile"
  echo
  echo " Other supported options are:"
  MANWIDTH=80 man chromium-browser | sed -e '1,/OPTIONS/d; /ENVIRONMENT/,$d'
  echo " See 'man chromium-browser' for more details"
}


Running with the -g parameter runs it with the gdb debugger. If you run it this way, do you see any error messages in the debugger?

---

### Post by brandon88tube on 2011-08-12
YAY! I figured out the problem after so sooooo long. I ended up using some of the switches from that website. The one that got me on the path to finding my answer was --enable-logging, that produced a file in .confg/chromium that contianed this: [2345:2360:5336896002:WARNING:file_descriptor_set_posix.cc(21)] FileDescriptorSet destroyed with unconsumed descriptors

I googled that and found this: [http://code.google.com/p/chromium/issues/detail?id=84640](http://code.google.com/p/chromium/issues/detail?id=84640)

I totally forgot that I had this in there and I guess an update screwed it up. Deleting the libpdf.so file solved my issue and I'm able to use the browser.

---

### Post by larrypg on 2011-08-12
Hello,
Just something to throw out there...your subject says chromium-browser but you say you have installed google chrome.  They are not the same program.

---

### Post by brandon88tube on 2011-08-12
I am talking about Chromium, but I did install Google Chrome to see if that might work. It is basically the same with Google's branding and some added plugins etc.

---

