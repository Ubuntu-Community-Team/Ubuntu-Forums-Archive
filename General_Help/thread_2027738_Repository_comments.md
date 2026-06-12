---
title: "Repository comments"
date: 2012-07-16
forum: General Help
---

### Post by BoogeyOfTheMan on 2012-07-16
Is it possible to add comments via the terminal when you add a repo?

It seems that there are a lot more PPA's around that I want to use than there used to be, and its hard to remember why I added certain ones. I like to add the name of whatever app I'm getting from it to the comments in case I decide to stop using that app for some reason.

---

### Post by claracc on 2012-07-17
Yes, if you want to edit your sources.list file:

gksudo gedit /etc/apt/sources.list

then you add a comment, you have to start the line with # symbol

Here is an old thread which can clarify: [http://ubuntuforums.org/showthread.php?t=844539](http://ubuntuforums.org/showthread.php?t=844539)

---

### Post by BoogeyOfTheMan on 2012-07-17
Thanks, I didnt think about editing the file directly. I was doing it through the Software Sources app.

What I meant though was something like:

sudo add-apt-repository thePPAi_want_to_add -comment this is the ppa for the widget app

---

### Post by claracc on 2012-07-17
You can add your ppa and a comment for it through the software sources menu, in other software (GUI) in system --> administration, you tick on add in the windows appearing, there you add the apt line and then, using the edit key you can add a comment to the ppa.

I give you a link explaining howto work with ppas: [http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

---

### Post by stinkeye on 2012-07-17
> **BoogeyOfTheMan said:**
> Is it possible to add comments via the terminal when you add a repo?

It seems that there are a lot more PPA's around that I want to use than there used to be, and its hard to remember why I added certain ones. I like to add the name of whatever app I'm getting from it to the comments in case I decide to stop using that app for some reason.
I understand what you mean and would also like a solution to this as well.

When someone gives you a line like...
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
```
I would like to be able to add **compiz-preproposed** as the comment
without having to do a second step of opening software-sources and adding the comment manually.

---

### Post by BoogeyOfTheMan on 2012-07-17
> **stinkeye said:**
> I understand what you mean and would also like a solution to this as well.

When someone gives you a line like...
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
```
I would like to be able to add **compiz-preproposed** as the comment
without having to do a second step of opening software-sources and adding the comment manually.

Exactly. I recently added a bunch of PPA's for various indicators and when one started acting up, I spent 30 min Googling them to figure out which one I got what app from so I could remove it after I uninstalled the app.

I tried reading about the available arguments for add-apt-repo, and from what I can gather, there is no function available to accomplish this. I'm wondering if it could be implemented via script. I'm planning on reading up on scripting some today to see if I can get an idea. If nothing else, I'll learn something new at least.

---

### Post by stinkeye on 2012-07-17
It's beyond my skill to script something but you may want to take a look at
the python script @ **/usr/bin/add-apt-repository**

From the script...
> <sourceline> - The apt repository source line to add. This is one of:
  a complete apt line in quotes, 
  a repo url and areas in quotes (areas defaults to 'main')
  a PPA shortcut.

  Examples:
    apt-add-repository 'deb [http://myserver/path/to/repo](http://myserver/path/to/repo) stable myrepo'
    apt-add-repository 'http://myserver/path/to/repo myrepo'
    apt-add-repository 'https://packages.medibuntu.org free non-free'
    apt-add-repository [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) 
    apt-add-repository ppa:user/repository

---

### Post by Vaphell on 2012-07-17
```
#!/bin/bash

if [ $# -lt 2 ]; then echo "2 parameters required (ppa string, label)"; exit; fi

ppastr="$1"
label="$2"

sudo add-apt-repository "$ppastr"
if [[ $ppastr =~ ppa:[a-z-]*/[a-z-]* ]]
then
  ppastr="ppa.launchpad.net/${ppastr#ppa:}/"
fi

sudo sed -ri "s/^(# *)?([^#]+)( .*$|$)/\1\2 #$label/" $( grep -l "$ppastr" /etc/apt/*.list /etc/apt/sources.list.d/*.list )
```

very crude script running *add-apt-repository <ppastring>* and then looking for the file where the string is located and adding #label.
Should work with ppa:user/name format, don't know what's with the other formats with urls. My 10.04 add-apt-repository complained that the strings are invalid, though the script is not hardcoded for ppa:user/name format and in theory other formats should work.

```
add-ppa.sh ppa:mozillateam/firefox-next "Firefox next PPA"
```
it doesn't detect if the repo is already installed (doesn't matter anyway) so as a side effect it can be used to rename the repo or add a name to it, while preserving enabled/disabled status (line started with # = disabled) - just run again with the same ppa string

---

### Post by BoogeyOfTheMan on 2012-07-17
Worked like a charm, you are a true gentleman and scholar sir.

---

### Post by Vaphell on 2012-07-18
small update because previous version would work incorrectly if the repo definition was in a file with multiple lines (like /etc/apt/sources.list)
```
#!/bin/bash

if [ $# -lt 2 ]; then echo "2 parameters required (ppa string, label)"; exit; fi

ppastr="$1"
label="$2"

sudo add-apt-repository "$ppastr"
if [[ $ppastr =~ ppa:[a-z-]*/[a-z-]* ]]; then ppastr="ppa.launchpad.net/${ppastr#ppa:}/"; fi

file=$( grep -l "$ppastr" /etc/apt/*.list /etc/apt/sources.list.d/*.list )
sudo sed -ri "/${ppastr////.}/ s/^(# *)?([^#]+)( .*$|$)/\1\2 #$label/" $file
echo ----------------------------------
grep "$ppastr" $file
```

---

