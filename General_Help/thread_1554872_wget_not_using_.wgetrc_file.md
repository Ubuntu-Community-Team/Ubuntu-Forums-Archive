---
title: "wget not using .wgetrc file"
date: 2010-08-17
forum: General Help
---

### Post by xmichielx on 2010-08-17
Hello,

I am using wget to grep some data from a .htaccess protected website.
I don't want to use the --http-user= and --http-password= variables in the script so I tried to create a ~/.wgetrc file which looks like:

http_user=username
http_password='password@12345'

Whenever I run my wget script, it will never use the http_user and http_password examples to login to th website.
I also tried to set the WGETRC example in ~/.bashrc and reopend a shell to make sure I have the latest system variables:

declare -x WGETRC="/home/username/.wgetrc"
declare -x WINDOWID="79692018"
declare -x XAUTHORITY="/var/run/gdm/auth-for-username-DEdSYJ/database"
declare -x XDG_CONFIG_DIRS="/etc/xdg/xdg-gnome:/etc/xdg"
declare -x XDG_DATA_DIRS="/usr/share/gnome:/usr/local/share/:/usr/share/"
declare -x XDG_SESSION_COOKIE="494b2befc00abdbd63a005574c572434-1282029494.424899-1490187015"

The script that I am running is as follows:

for i in `cat iplist.*`; do
echo -n "Ip-adress $i is active: " 
WGETRC=/home/username/.wgetrc
wget -O - 2>/dev/null "http://htpasswordprotectedurl/racktables/?page=ipaddress&ip=$i" | grep Allocations| awk '{ print $4 }'| sed 's/class=tdleft>//' | sed 's/<\/td><\/tr>//' ;done | grep -v 0$

It will not work, if I hardcore the --http-user=username and --http-password='password@12345', it will work like a charm.

What am I doing wrong?

I am using Ubuntu:
cat /etc/debian_version 
squeeze/sid

64 bit.

Thanks for any help.

Kind Regards,

Michiel

---

### Post by AlphaLexman on 2010-08-17
Copy the wgetrc file from /etc/ to your home directory ->
```
cp /etc/wgetrc ~/.wgetrc
```
It is mostly commented out, but it looks like it has 'spaces' surrounding the equal sign (=) where you don't.

---

### Post by xmichielx on 2010-08-17
Hmm I also tried with the spaces but that also didn't work.
Can someone confirm that it works at his/hers machine for htaccess protected websites?

---

