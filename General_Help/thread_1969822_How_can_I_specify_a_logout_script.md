---
title: "How can I specify a logout script?"
date: 2012-04-30
forum: General Help
---

### Post by Paddy Landau on 2012-04-30
In Natty 11.04, I could specify actions to take when logging out by adding commands to [FONT=Lucida Console]/etc/gdm/PostSession/Default[/FONT].

But now, in 12.04 (fresh installation, fully updated), the folder [FONT=Lucida Console]/etc/gsm[/FONT] no longer exists.

How do I specify a logout script?

---

### Post by papibe on 2012-04-30
Hi Paddy Landau.

Precise is not using [gdm]("http://en.wikipedia.org/wiki/GNOME_Display_Manager") anymore. Instead, [lightdm]("http://en.wikipedia.org/wiki/LightDM") is the defualt display manager.

You still will be able to set your login, and logout script, but in a slightly different way. The config file now is:
```
/etc/lightdm/lightdm.conf
```
And the relevant fields are:
```
session-setup-script
session-cleanup-script
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Paddy Landau on 2012-05-01
Thank you, papibe.

That does indeed work.

There is a twist, though: the script runs as root and yet ${USER} and ${HOME} are set for the user who is logging in or out.

Therefore, to run a command as the required user, you have to use:
```
su "${USER}" --command "command-to-run"
```

---

### Post by Paddy Landau on 2012-10-25
I am reopening this thread, because the previously-described solution no longer works.

I have tried everything that I can think of (which is not much), but the specified logout script just no longer runs.

So, the question again is:

How do I specify a logout script?

---

### Post by zombifier25 on 2012-10-25
There's a quick and probably dirty solution: Add the command to .bash_logout . It's like .profile, but it executes when a user logs out.

---

### Post by Paddy Landau on 2012-10-25
> **zombifier25 said:**
> There's a quick and probably dirty solution: Add the command to .bash_logout . It's like .profile, but it executes when a user logs out.
Thanks, but that does not work for Ubuntu.

.bash_logout is executed when logging out from a console (e.g. Ctrl+Alt+F1), but not from a GUI session.

---

### Post by papibe on 2012-10-25
Did you upgrade to 12.10, or just stopped working after a regular update?
Regards.

---

### Post by pqwoerituytrueiwoq on 2012-10-25
the script does run just after the user name is no longer in $(users) 
you have to use a alternative way to get the current user, i did this a really messy way
my logout script:
```
#!/bin/bash
ogg123 -d pulse /usr/share/sounds/ubuntu/stereo/desktop-logout.ogg &> /dev/null &
#echo "`date`" > /var/log/xfce-logout-script
pid="`pgrep -f gmusicbrowser | head -1`"
#echo "pid = $pid" >> /var/log/xfce-logout-script
if [ "0$pid" -gt "0" ]; then
    user="`ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}'`"
#    echo "user = $user" >> /var/log/xfce-logout-script
    sudo -u $user gmusicbrowser -cmd Quit
fi
killall inhibit-powersave
killall Compiz
killall pause-music
rm /tmp/compizLog
```

---

### Post by Paddy Landau on 2012-10-26
And&#8230;

Now it is working.

Sorry, I do not understand why. Yesterday, and for a few weeks prior to that, it was not working. Today it is working. :confused:

I have no clue what could have made the difference. I had tried  restarting the computer yesterday, so that was not the problem. I must  have done something; I just don't know what.

I shall remark this thread solved, and keep an eye on the logout script.

Thank you all for your input.

To answer pipibe's question:
> **papibe said:**
> Did you upgrade to 12.10, or just stopped working after a regular update?
No; back in May, this was a fresh installation of 12.04, which I have kept fully-updated. I have not upgraded to 12.10.

> **pqwoerituytrueiwoq said:**
> you have to use a alternative way to get the current user, i did this a really messy way
I did it a slightly easier way, which would work for all users.

[LIST=1]
[*]In the file [FONT=Lucida Console]/etc/lightdm/lightdm.conf[/FONT], I added the following line (anywhere under the [FONT=Lucida Console][SeatDefaults][/FONT] section).
```
session-cleanup-script=/opt/gScripts/logout-lightdm
```
[*]The file [FONT=Lucida Console]/opt/gScripts/logout-lightdm[/FONT] contains the following.
```
#!/bin/bash

# Run user's ${HOME}/bin/bash_logout if it exists and is executable.

if [[ -x "${HOME}"/bin/bash_logout ]]
then
    # Called from LightDM, this runs as root, so use su to revert to the user.
    su "${USER}" --command "${HOME}"/bin/bash_logout
fi
```
[/LIST]
Then, if the user has an executable file called [FONT=Lucida Console]bash_logout[/FONT] in his own [FONT=Lucida Console]~/bin[/FONT] folder, it will execute under his own user.

I did not use [FONT=Lucida Console]${HOME}/.bash_logout[/FONT], because that is used specifically for exit from a console.

Off-topic: @pqwoerituytrueiwoq: You must curse your user name every time you have to log in to a new computer! :)

---

### Post by Lars Noodén on 2012-10-26
There is a bug report related to the problem you just solved.  

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1044485](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1044485)

It might have gone a bit easier if there had been either a manual page for lightdm.conf(5) or an annotated default lightdm.conf.

---

### Post by Paddy Landau on 2012-10-26
> **Lars Noodén said:**
> There is a bug report related to the problem you just solved.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1044485](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1044485)

It might have gone a bit easier if there had been either a manual page for lightdm.conf(5) or an annotated default lightdm.conf.
Thanks for pointing out the bug. I have added my vote.

---

### Post by s1baker on 2012-10-29
this is weird.
I just looked at my /etc/lightdm/lightdm.conf file:

```

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

note "SeatDefaults", and this is the first time I have opened the file.

---

### Post by Paddy Landau on 2012-10-30
> **s1baker said:**
> note "SeatDefaults", and this is the first time I have opened the file.
Sorry, my mistake — it is indeed "SeatDefaults". I've corrected my previous post.

---

### Post by Paddy Landau on 2012-11-26
I am reopening this thread, because I have a problem.

The [FONT=Lucida Console]session-cleanup-script[/FONT] option is failing, not because it fails to run, but because I am using an encrypted folder.

As soon as I log out, the decrypted folder is dismounted, so the [FONT=Lucida Console]session-cleanup-script[/FONT] cannot run on the decrypted folder.

In other words, [FONT=Lucida Console]session-cleanup-script[/FONT] is run *after* logging out instead of beforehand.

How can I resolve this problem?

**EDIT:** I have spotted [another thread]("http://ubuntuforums.org/showthread.php?t=1918649"), and I am asking the question there.

---

### Post by cmcanulty on 2012-11-26
I put these aliases in my .bash.rc file


```
alias lox='xfce4-session-logout --logout'
alias log='gnome-session-quit'

alias lol='lxsession-logout'

```

---

### Post by Paddy Landau on 2012-11-27
> **cmcanulty said:**
> I put these aliases in my .bash.rc file…
Sorry, I don't understand how this helps.

---

### Post by nezero on 2013-01-14
Any solution to this yet? I am also trying to run a script before logout ([for a different reason]("http://ubuntuforums.org/showthread.php?p=12454481#post12454481")) and would be keen to know if you have found a workaround.

---

### Post by Paddy Landau on 2013-01-14
> **nezero said:**
> Any solution to this yet?
Yes and no!

I still do as described in [post=12318858]post #9[/post].

However… it works only when restarting. When just logging out (not restarting), it fails.

Debugging shows that when logging out, user's decrypted folder is immediately dismounted, i.e. no longer decrypted. But when restarting, there is a delay, and the user's decrypted folder is left mounted for a while.

Bizarre!

I wish I knew the answer — how to access the user's bin file before dismounting, whether restarting or just logging out.

---

### Post by experimancer on 2013-03-08
Hi,

I am trying to solve the same problem; how to run a user specifig logout-script when signing of from X-session in Ubuntu. 

I also found out (by accident actually), that lightdm-set-defaults and its configuration file lightdm.conf are the starting point. However, as the lightdm does not have proper documention in my system (12.04.02, Ubuntu Precise Pangolin), I, too, added my comments to the relavant bug in Launchpad ([https://bugs.launchpad.net/precise-backports/+bug/883189](https://bugs.launchpad.net/precise-backports/+bug/883189)). 

While it is not even sure that the possible fix will be backported to Precise, I am wondering now where did you actually get the relevant information about the lightdm config options (as in your post #9)?

Thanks for any information..

---

### Post by Paddy Landau on 2013-03-08
> **jjaone said:**
> … I, too, added my comments to the relavant bug in Launchpad ([https://bugs.launchpad.net/precise-backports/+bug/883189](https://bugs.launchpad.net/precise-backports/+bug/883189)).
Thanks for the link to the bug. I have added both my vote and a comment. (Did you add your vote? The green writing near the top-left of the page.)

> **jjaone said:**
> … I am wondering now where did you actually get the relevant information about the lightdm config options (as in your post #9)?
Sorry, I don't remember, but I would have searched this forum and, probably, Googled to find other forums. Maybe [AskUbuntu]("http://askubuntu.com/") helped.

I have more information. The script runs when I log out by restarting the machine, but it does not run when I merely log out without restarting (so, log out and then restart will not run the script). I do not know how to solve that problem.

---

### Post by dwok on 2013-06-21
My workaround (also using encrypted $HOME)
(as root)
mv /bin/umount /bin/umount.d
vi /bin/umount 
put in this:
#!/bin/bash
PASS=$*
if [[ ! `/usr/bin/w | grep gnome-session` ]]; then
# need to check for active sessions as su and exiting from shells can call umount 
    /bin/logout-lightdm # containing suggested scipt pointing to /home/usr/bin/.bash_logout
fi
/bin/umount.d $PASS
exit 0

then 
chmod 4755 /bin/umount

Not nice but logout and reboot worked. Or has the issue been fixed?

---

### Post by Paddy Landau on 2013-06-21
> **dwok said:**
> My workaround….
Thanks for posting your solution.

> **dwok said:**
> … has the issue been fixed?
The issue that I still have (as explained at the end of [post=12547499]post #20[/post]) still remains. Otherwise, it works. Does your solution work when logging out and in again?

By the way, your last line:
```
/bin/umount.d $PASS
```
You need to quote the password in case it contains certain special characters, thus:
```
/bin/umount.d "${PASS}"
```

---

### Post by dwok on 2013-06-21
PASS are just the parameters that are passed on when using umount
eg: umount /media/disk
so I was not expecting any special characters but thanks and I will change it just in case.
My work around is a wrapper that is called when the system is using umount.
As in this case when you log out your .privat will be un-mounted.
So the answer is yes it works using logout and reboot because I'm telling the system
to do my stuff and then pass on the umount command.
Tested on 12.04 

Hope this clarifies. :D

---

### Post by Paddy Landau on 2013-06-22
Thanks for the reply, dwok.

In testing your method, I see that neither [FONT=lucida console]${USER}[/FONT] nor [FONT=lucida console]${HOME}[/FONT] is set for the user who is logging out. Therefore, your method will work only for a single-user machine where you know the user beforehand.

Also, where I suggested that you use [FONT=lucida console]"${PASS}"[/FONT], this is not quite correct, as there may be multiple parameters. If none of the parameters contains spaces, you can use [FONT=lucida console]${PASS}[/FONT]; but if any parameter contains a space (which is possible, albeit rare), it will fail.

Instead, you will need to use [FONT=lucida console]"${@}"[/FONT], without using [FONT=lucida console]PASS[/FONT] at all:
```
/bin/umount.d "${@}"
```

---

### Post by dwok on 2013-06-23
Correct I only had one user.
I have now set up a few more (without encrypted $HOME but umount is called anyway) I have modified my /bin/umount to execute a script in /TEST
You are right with that /bin/umount does not have $USER or $HOME set, but funny enough when it then calls the test script they are set again:
### logout dwok1
start Umount:      <- echo from /bin/umount
Umount id:
uid=0(root) gid=1001(dwok1) groups=0(root),1001(dwok1)  <- interesting to see that the last row from "id" shows the user
root
UMOUNT calling new_test.sh
START new_test.sh                                   <- begin of script called by /bin/umount
clean USER:  dwok1                                   <- $USER is set
clean HOME:  /home/dwok1                         <- $HOME is set 
Next lines from id
uid=0(root) gid=1001(dwok1) groups=0(root),1001(dwok1)    <- again root user is executing but last entry is our actual user 
END new_test.sh                                       <- script ended
UMOUNT now unmounting                            <- back to umount to execute the umount command.  
### logout dwok3
start Umount:
Umount id:
uid=0(root) gid=1003(dwok3) groups=0(root),1003(dwok3)
root
UMOUNT calling new_test.sh
START new_test.sh
clean USER:  dwok3
clean HOME:  /home/dwok3
Next lines from id
uid=0(root) gid=1003(dwok3) groups=0(root),1003(dwok3)
END new_test.sh

So this should work for your multiple users logging out.
you need to check if the "gnome-session" (use "w" and grep for user don't use "ps") is still running for that user - only if not then 
execute your stuff, otherwise it will always execute.

During shutdown umount is called 6 times - during the first time $USER and $HOME is set
after that is it no longer set. 

I think this info should be enough to create a script - it is getting late for me now so I will try one another day.

Please let me know how your testing went.    :)

---

### Post by dwok on 2013-06-23
btw ${PASS} works with spaces nicely:
more TEST.sh 
#!/bin/bash
PASS=$*

echo "P: #${PASS}#"

root@my-ubox:/TEST# ./TEST.sh with -d and lots -w of spaces
P: #with -d and lots -w of spaces#

---

### Post by Paddy Landau on 2013-06-23
> **dwok said:**
> … You are right with that /bin/umount does not have $USER or $HOME set, but funny enough when it then calls the test script they are set again…
That's all interesting. It is worth trying.

> **dwok said:**
> btw ${PASS} works with spaces nicely..
There's something there that I'm not understanding. I'll have to test it thoroughly to understand. If you look at the difference between [FONT=lucida console]$*[/FONT], [FONT=lucida console]"$*"[/FONT], [FONT=lucida console]$@[/FONT] and [FONT=lucida console]"$@"[/FONT], you will understand my confusion as to how your version manages to work.

---

### Post by Paddy Landau on 2013-06-23
> **dwok said:**
> btw ${PASS} works with spaces nicely…
I'm not getting the same results as you. Here's my test:

Save the following script: [ATTACH]244059[/ATTACH]
Because of the forum restrictions, it is compressed. Decompress it and ensure that the executable bit is set with: [FONT=lucida console]chmod +x testQuotes[/FONT]

The script tests every variation of [FONT=lucida console]${*}[/FONT], [FONT=lucida console]"${*}"[/FONT], [FONT=lucida console]${@}[/FONT], and [FONT=lucida console]"${@}"[/FONT], both from a variable and directly, and calling the receiving script (in this case a function) both with quotes and without (see the script for details).

Now, call the script with the following line (note the multiple spaces within the third parameter):
```
./testQuotes a 'b c' '   d   e   f   '
```

The receiving script displays what it receives in each test case. What we want is for it to receive three parameters, viz. [FONT=lucida console]'a'[/FONT], [FONT=lucida console]'b c'[/FONT], and [FONT=lucida console]'   d   e   f   '[/FONT] (the latter with multiple spaces included).

However, when you run the script, only the last one works correctly — exactly as predicted by the documentation.

That is why I am confused as to how you are getting correct results from [FONT=lucida console]${PASS}[/FONT].

---

### Post by dwok on 2013-06-24
No need to be confused - I'm not getting the correct results - I'm getting just results "for the umount' command - your syntax is the correct way.

I hope I have attached a file with my scripts and log files, tested and working for multiple users calling $HOME/bin/exit_script.sh upon logout and reboot.
With umount /cdrom and /media/xx etc.still working and not executing the exit_script.sh in each $HOME.

I'm sure there are some syntax flaws within the scripts  - this is purely about function.
 If you could please confirm if they are doing the job and feel free to provide me the scripts with a correct syntax.

:)

---

### Post by Paddy Landau on 2013-06-24
dwok, thanks for the scripts.

It may be a couple of days before I can look at this.

---

### Post by spi@gmxpro.de on 2013-07-11
Just a quick thought - why hassle around with unmounting/restarting service whatsover on user logout and not checking for anomalies on user login instead and unmounting/restarting service then?

I mount some EncFS folders on user login which I don't unmount on logout. After logging in again the automatic mount in almost all cases doesn't work anymore. I check for this to happen and unmount (fusermount -zu ...) the .fuse folder on user login first before I do the mount again.

---

