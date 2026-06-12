---
title: "Command line user privileges"
date: 2012-01-23
forum: General Help
---

### Post by Floore on 2012-01-23
Hi,

I am rolling out a Ubuntu kiosk solution for a client of mine and I have created a script to run post-install that will set up the environment.

I have included a simple useradd script that will create the user and assign them a password but I need to create the user's permissions (i.e. nothing), and alter the logon screen to not show the user list and not prompt for the limited user's password when they login. I need to run this from a script though, and I don't know how to do it. Can anyone help me?

---

### Post by Floore on 2012-01-23
OK, I have managed to somehow figure some of it out in the last few minutes, despite having browsing the web for answers for a few hours now!

I have done the following:

Created user dave, and assigned him a password
Created a new group with no permissions (I didn't realised new groups defaulted to having no extra permissions than necessary)
Added dave to the group
Given dave sudo permissions to shutdown

I accomplished this as follows:


if [ $(id -u) -eq 0 ]; then
	username=dave
	password=google
	egrep "^$username" /etc/passwd >/dev/null
	if [ $? -eq 0 ]; then
		echo "$username exists!"
		exit 1
	else
		pass=$(perl -e 'print crypt($ARGV[0], "password")' $password)
		useradd -m -p $pass -g noper $username
		[ $? -eq 0 ] && echo "User has been added to system!" || echo "Failed to add a user!"
	fi
else
	echo "Only root may add a user to the system"
	exit 2
fi
echo "dave ALL=NOPASSWD: /sbin/shutdown" >> /etc/sudoers


Now all I need to do is somehow prevent the users list appearing, and prevent dave's account requiring a password at the logon screen.

This is something I just can't find. Any ideas would be helpful :)

---

