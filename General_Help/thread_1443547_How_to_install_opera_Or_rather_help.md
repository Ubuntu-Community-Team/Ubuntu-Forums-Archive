---
title: "How to install opera? Or rather help?"
date: 2010-03-31
forum: General Help
---

### Post by Chris Psycho on 2010-03-31
Well just got onto linux...:p Its kinda been just sittdng on my desk so decided to start it off :)

Though first things first, having some trouble installing Opera.

After following instuctions here: [http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian](http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian)

After running this in the terminal: gpg --keyserver subkeys.pgp.net --recv-key 6A423791

I get a error 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver.ubuntu.com --recv-keys 881574DE
gpg: Invalid option "--keyserver.ubuntu.com"


Where am I going wrong?

And why is'nt there a 'ubuntu' installer that does this for you?

Must this be done to every progarm I want to add?

Thank you :p looking forward to the Ubuntu world!

---

### Post by zvacet on 2010-03-31
[Here]("https://help.ubuntu.com/community/OperaBrowser")

---

### Post by Luke771 on 2010-03-31
This isnt a complete answer but if you manage to make good use of it you probably won't need to ask how to install a downloaded program any more ;)

- google opera
- download opera for linux in .deb format
- in a terminal, cd to the directory where the .deb package is, then do: sudo dpkg -i opera.xxx.deb
- It will probably output that it cant be installed because some required packages are missing, and lists the missing packages
- copy the missing packages names and do: sudo apt-get install [paste package names here]

After completing the installation of the required packages, do sudo dpkg -i opera.xx.deb again

---

### Post by vrchards on 2010-03-31
Here is the finest way to install Opera browser in linux,
First download latest Opera .deb package from here

Once you downloaded the .deb file install this file using the following command

    sudo dpkg -i opera_10.00.4585.gcc4.qt3_i386.deb

Install flash plugin using the following command

    sudo apt-get install flashplugin-nonfree

If you have problem with your videos follow this procedure

Open Opera

Click on Tools > Preferences >go To The advanced tab

Click on Downloads on the left side

find the one that says application/x-shockwave-flash

Click Edit at the bottom it says Use Plugin from the pull down menu

select the one that says: ‘Shockwave Flash - /usr/lib/mozilla/plugins/flashplugin-alternative.

so’ if it doesn’t work you can try a different one from the pull down menu

Click OK and exit

Install Java plugins using the following command

    sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin ubuntu-restricted-extras

---

### Post by kaldor on 2010-03-31
[http://www.opera.com/browser/download/?os=linux-i386&ver=10.10&local=y](http://www.opera.com/browser/download/?os=linux-i386&ver=10.10&local=y)

Or you can just use that .deb and skip all that stuff altogether lol


Note: you won't usually need to use the command line in Ubuntu these days, but don't think of it at all like the Windows prompt. That thing was scary on Windows because it was associated with geeks and system alterations. Linux has some really simple to use commands.

---

### Post by Chris Psycho on 2010-04-08
Thank you! 

On another note... How can I quickly look up my own posts (here on ubuntuforums.org)? Had some trouble finding this one so..

---

### Post by mkvnmtr on 2010-04-08
If you download the default download for 10.10 all you need to do is double click it. It will even give you a repository.
I have found Opera 10.52 for linux. It is much faster and seems just as stable. It is a daily build kind of thing and double clicking installed it but I do not see a repository. I would recomend 10.52, it is great.

---

