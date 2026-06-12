---
title: "Creating Nmap Shortcut"
date: 2012-07-10
forum: General Help
---

### Post by securitydude on 2012-07-10
I want to create a shortcut on my desktop for nmap. I wrote a bash script but the problem is that the terminal window just disappears after nmap command is executed.

I also tried gnome-desktop-item-edit --create-new ~/Desktop and gave exact path of nmap. However nothing happens when I double click the shortcut.

Any ideas what I need to do in order to directly load nmap in terminal by just clicking the icon on desktop?

Thanks in advance.

---

### Post by MG&amp;TL on 2012-07-10
```
gnome-terminal -e "Your command here"
```

should work.

---

### Post by securitydude on 2012-07-10
> **MG&TL said:**
> ```
gnome-terminal -e "Your command here"
```

should work.

Sorry for being a noob but where do I put this. Tried putting this in terminal but nothing happens.

---

### Post by Habitual on 2012-07-10
> **securitydude said:**
> I want to create a shortcut on my desktop for nmap. I wrote a bash script but the problem is that the terminal window just disappears after nmap command is executed.

I also tried gnome-desktop-item-edit --create-new ~/Desktop and gave exact path of nmap. However nothing happens when I double click the shortcut.

Any ideas what I need to do in order to directly load nmap in terminal by just clicking the icon on desktop?

Thanks in advance.

the problem can be solved by making an interactive .sh script file and then using the suggested gnome-terminal -e "/path/to/script.sh"

This is because iptables run "as is" requires input to do its work.
so, If I may suggest something along these lines...

```

#!/bin/bash

echo -n "enter the IP address: "
read ANSWER1
for periods in "$@"
  do
   **[COLOR=Red]iptables -L -n "$ANSWER1"[/COLOR]**
  done

```save the file as say ~/iptshell.sh
In terminal > 
```
chmod 700 ~/iptshell.sh
```Then make a desktop launcher for```
 gnome-terminal -e /full/path/to/iptshell.sh 
```Every time you run the desktop shorty, you'll be prompted for the ip to scan.
NOTE: [COLOR=Red]iptables -L -n "$ANSWER1" code will/may require some code[/COLOR] to keep the terminal open, I believe.

HTH.

subscribed with interest...

---

### Post by SeijiSensei on 2012-07-10
> **securitydude said:**
> I want to create a shortcut on my desktop for nmap. I wrote a bash script but the problem is that the terminal window just disappears after nmap command is executed.

You'll also need to tell it to run as root.  There are only a few things you can do with nmap, like pingscans, unless you run it with root privileges.

---

