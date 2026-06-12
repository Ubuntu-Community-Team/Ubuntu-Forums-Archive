---
title: "need help with script/sudo"
date: 2010-09-20
forum: General Help
---

### Post by mkris23 on 2010-09-20
hey,

we have been running a small network with about 400-500 users. most of our user run windows with a small minority of them using linux, mostly ubuntu. we also have an upgrade server set up using the apt-cacher. beacuse of the growing number of ubuntu  users, we needed to shift our cache from the present one to a better computer. we did this yesterday. usually, a small number (3 or 4) of us do the ubuntu installations and we manually change the /etc/apt/apt.conf.d/01proxy file to point to our ubuntu update server. now that we have changed the update server, we need to get everyone to change the contents of the 01proxy file to point to our new server. since many of our users are not highly tech savvy, we decided to write a script that would remove the present 01proxy file and replace it with a file containing the ip address of the new server. we dont want the users to go to terminal and run the shell script from there. ideally, we would like them to just download the script from us and execute it by double clcking it. however, we are not able to get this to work properly with the script we wrote.

```

/bin/bash
echo 'Ubuntu Proxy Change Script'
read -p 'Press Enter to Continue'
sudo rm /etc/apt/apt.conf.d/01proxy
sudo echo 'new.proxy' > /etc/apt/apt.conf.d/01proxy
clear
echo 'Your settings have been changed. Thank You.'
read -p echo 'Press Enter to Continue'
exit
```any help would be appreciated. thank you.

---

### Post by perspectoff on 2010-09-20
How about this thread?

[https://bbs.archlinux.org/viewtopic.php?pid=298921](https://bbs.archlinux.org/viewtopic.php?pid=298921)

---

### Post by Ayuthia on 2010-09-20
You might try changing:
```

sudo echo 'new.proxy' > /etc/apt/apt.conf.d/01proxy

```
to this:
```

echo 'new.proxy' | sudo tee /etc/apt/apt.conf.d/01proxy

```
Based on this information, it will overwrite what is in 01proxy with 'new.proxy'.

In your version, you are only providing the sudo property to the command on the left when you really need the command on the right.  The script is most likely not able to access 01proxy because you need admin access to change the data in 01proxy.

In the revised version, the sudo command is set to the tee command which will be able to write to the file.

I hope that helps.

EDIT:
By the way, you might want to change the first line to be:
```

#!/bin/bash

```

---

### Post by mkris23 on 2010-09-20
thanks for the replies. my issue is more with how to get a terminal window to open up so people can type in their passwords. the problem right now is that they will inevitably have to go to terminal and type in commands to make this run. is there any way that i can make a terminal window open up, so they can enter their password, and nothing more.

---

### Post by bodhi.zazen on 2010-09-20
> **mkris23 said:**
> thanks for the replies. my issue is more with how to get a terminal window to open up so people can type in their passwords. the problem right now is that they will inevitably have to go to terminal and type in commands to make this run. is there any way that i can make a terminal window open up, so they can enter their password, and nothing more.

Use gksu rather then sudo.

---

### Post by sisco311 on 2010-09-20
> **bodhi.zazen said:**
> Use gksu rather then sudo.

+1

Try something like:
```
gksu --message "Enter your password to update your proxy settings." "bash -c 'echo new.proxy > /etc/apt/apt.conf.d/01proxy'"
```

or with zenity&pkexec:
```
#!/bin/bash

function err()
{
  if [ -e /usr/bin/zenity ]; then
    zenity --error
  fi
}

if [ -e /usr/bin/zenity ]; then
  zenity --info --title "Ubuntu Proxy Change Script" --text "Ubuntu Proxy Change Script\n\nPress OK to Continue."
  if (( $? )); then
    err
    exit 1
  fi
fi

**echo 'new.proxy' | pkexec tee /etc/apt/apt.conf.d/01proxy**

if (( $? )); then
  err
  exit 2
fi

if [ -e /usr/bin/zenity ]; then
  zenity --info --title "Ubuntu Proxy Change Script" --text "Your settings have been changed. Thank You!\n\nPress OK to Continue."
fi

exit 0

```

---

### Post by mkris23 on 2010-09-21
yeah, the last bit of code seems to have done the trick. thanks a lot. :)

---

