---
title: "How do you execute a script when unlocking screen?"
date: 2011-08-05
forum: General Help
---

### Post by opus1 on 2011-08-05
I would like to wake my file server by sending a magic wol packet when a user unlocks the screen of another computer.  After a couple of weeks, I have not found a reliable way to do this.  Any suggestions?

I keep finding variations of a perl script to look for the screensaver status (e.g.[here]("http://superuser.com/questions/205334/how-do-you-get-ubuntu-to-automatically-run-a-program-every-time-the-screen-is-unl") and [here]("http://www.linuxquestions.org/questions/fedora-35/start-and-stop-script-with-screensaver-728498/")) but this method only seems to work once-in-a-while for me so I have given up on it.

Another thing I have tried is to run a cron job that looks for the "slideshow" screen saver using pgrep, but it appears that slideshow is terminated when the screen shuts off.  Besides, if I change screensavers, it will break the script.

I thought of setting up a script to look for the password dialog box or the password checking process, but I can't find what those process names are called.

I also tried using gnome-screensaver-command -q which would list if the screensaver was active or not, but I couldn't get it to return anything when running it as a cron job.  Plus, I think it will have the same problem as my "slideshow" solution above.

It seems like the best solution is to look for the password dialog or password checking processes.  If anyone can help me make any of the ideas in this post work, I would be grateful.

---

### Post by papibe on 2011-08-06
If you are running 10.4, [this]("http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html") may work.

Regards.

---

### Post by opus1 on 2011-08-09
Thanks for the idea!  It looks like it would work, but I had already found another solution.  

For anyone interested, here's what I did: I looked at the logs (specifically /var/logs/auth.log) and saw that an entry is made when ever the password is checked and accepted.  My log said:
```
Aug  7 14:10:57 mumble gnome-screensaver-dialog: gkr-pam: unlocked login keyring
```

Ultimately I found an application called "Swatch" which monitors a log for you and will run a script when a string that you specify appears in that log. Swatch requires a config file (.swatchrc), and mine looks like this:
```
watchfor /unlocked login keyring/
	exec /root/.gnome2/nautilus-scripts/wakeServer
```
where "/unlocked login keyring/" is the string to look for and "exec" defines the script to run when it is found. My wakeServer script looks like this:
```
#!/bin/bash

#wake the server
wakeonlan AA:BB:CC:DD:EE:FF

#record info in the log file
myVar="woke server at login:"
echo "$myVar">>/home/me/.serverWake.log
date>>/home/me/.serverWake.log

```
where "AA:BB:CC:DD:EE:FF" is the MAC address of my server.

Swatch will need to be entered as a start-up application (create an entry in System | Preferences | Startup applications called "runSwatch" and make the command "swatch --tail-file /var/log/auth.log --daemon". (In Debian, only root can read logs So the start up command needs to be prefaced with "sudo" and swatch will need to [be added to the sudoers file without a password]("https://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/"). In Ubuntu it appears non-root users can read logs. There could be a security issue with granting password-less access to swatch, but in my case it seems acceptable). 

So far it has worked perfectly!

---

### Post by opus1 on 2011-08-09
Another potential solution I found, but couldn't get to work (my scripting skills weren't up to snuff):

I learned that ```
tail -f
``` will monitor a file and print out the last x lines when it changes. So if I did a ```
(tail -f /var/log/auth.log & ) | grep -i "unlocked login keyring"
```, it would print out only those lines I was looking for. But i couldn't figure out how to fire off a command or script from that. I found a script at [http://www.unix.com/shell-programming-scripting/8681-using-tail-f.html]("http://www.unix.com/shell-programming-scripting/8681-using-tail-f.html") that was supposed to accomplish what I wanted (in this example it writes mail to a user, but could be adapted to firing off a script):
```
#! /bin/bash

search_word="search terms"
write_user=user_id

#read the last line (n1) of the log, assign the last line to a variable (output_line) and send mail
#to a user (write $write_user) with the output line in it
tail -n1 -f /path/to/log |&
while read -p output_line; do
 [[ $output_line == *"$search_word"* ]] && {
  print "$output_line" | write $write_user
  }
done
```
The assignment of the last line to the variable output_line never seemed to work.

---

