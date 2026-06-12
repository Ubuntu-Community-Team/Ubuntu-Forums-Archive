---
title: "disable recent documents in ubuntu 11.10?"
date: 2011-10-15
forum: General Help
---

### Post by fwin on 2011-10-15
Hello everyone,

the title says it all, anyone has any idea how to do this?

thanks in advance!

---

### Post by fwin on 2011-10-16
anyone?

---

### Post by hijacker777 on 2011-10-17
Delete history:

cd ~/.local/share
        rm recently-used.xbel
        touch recently-used.xbel

Disable:
cd ~/.local/share
        sudo chattr +i recently-used.xbel

Re-Enable:
cd ~/.local/share
        sudo chattr -i recently-used.xbel

[http://www.linux-survival-blog.de/2011/10/ubuntu-11-10-zuletzt-verwendet-loschen-recent-files/](http://www.linux-survival-blog.de/2011/10/ubuntu-11-10-zuletzt-verwendet-loschen-recent-files/)

---

### Post by mr.generic.user on 2011-10-19
I have recently switched to LMDE because I hate unity, but this (or a modified version) should work.  I wrote a shell script. it requires inotify-tools, but here is the code:

```
#!/bin/bash
recentFile="$HOME/.local/share/recently-used.xbel";
hasInotifyTools=$(type -P inotifywait);
if [ ! -z $hasInotifyTools ]; then
	echo "$recentFile";
	while true; do
		while inotifywait $recentFile; do
			if [ -s "$recentFile" ]; then echo "clearing file $recentFile"; cat /dev/null > $recentFile; fi
		done
	done
else
	echo "Please install inotify-tools...";
fi
```

I intend to add it to my session startup.

Hope it helps...

---

### Post by WorLord on 2011-10-19
Install "Activity Log Monitor" from the Zeitgeist PPA.  

Then turn logging off.

---

### Post by fwin on 2011-10-19
thank you very much everyone I will try your suggestions.:)

---

### Post by fwin on 2011-10-26
I was not able to use  "Activity Log Monitor" because I could not find any GUI that would allow me to modify settings, etc.. I also could not find enough documentation to learn how to use this program. Besides the "recent documents" issues, I was having other problems with 11.10 (computer was freezing at random times, etc..) and so I decided to uninstall it.

thank you all for your help!

---

### Post by anjoze on 2012-03-16
Finaly!!

sudo apt-get install activity-log-manager

---

### Post by ruhil on 2012-04-01
If you are using unity, you can make unity not to show your history by deleting the file used to show your history.
 sudo rm /usr/share/unity/lenses/files/files.lens
Now unity cannot show your history in your dash home.
Hope this helps someone :).

---

### Post by HiImTye on 2012-04-01
delete ~/.local/share/recently-used.xbel and make a folder with the same name
```
rm ~/.local/share/recently-used.xbel
mkdir ~/.local/share/recently-used.xbel
```

---

