---
title: "Log-in trouble"
date: 2012-06-24
forum: General Help
---

### Post by CalvinBaron on 2012-06-24
I've encountered a frustrating problem and am in dire need of some support, here it goes:

Three days ago I installed Lubuntu on an old Dell Inspiron 510m, the installation went very smoothly and I worked with the system for two days until yesterday morning I started the computer, the log-in screen appeared, I selected my username (no pass required), expected my desktop to appear but instead the screen went black for a moment and I was brought back to the log-in screen. There I tried to log in several times more but failed at each attempt. I've found several other forums touching upon this, or a very similar, problem but nowhere did I come across any answer that could solve it (except a complete re-install).

In short the events occur in this sequence:
log-in screen appears > click username > screen goes black > log-in screen reappears > click username... and so on in a circle.

Note: I am a complete novice to linux and have absolutely no clue as to what could be done to fix this problem.

Any help will be much appreciated. :smile:

---

### Post by jmfal on 2012-06-24
You should not have been able to complete the installation without a password.

The best bet is to reinstall and give yourself a password, and  a password for "sudo"

They can be the same password. 

Here is a link to add/change a password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by CalvinBaron on 2012-06-24
Thank you for your reply. ):P

In setting up my account I did create a password, but later under "System Tools > Users and Groups" I checked the "Don't ask for password on login" box and successfully logged-in a few times without the need of entering a password on each occasion. 

Lubuntu worked fine like this for almost two days, until this morning. Now, the strange thing is that I can still successfully enter the "Guest Account" where I've created another account with administrator privileges (and a pass) which too I can enter without the slightest trouble. 

What I still need to find is a way of getting into my original account again. 

As for now the sequence as described in my first post keeps affecting it.

Thanks again.

---

### Post by jmfal on 2012-06-24
I'm not sure whats going on, I'll have to look around for a solution.

In the meantime try to login to your other administer account and see if there are some updates, install if you can, then try to log back in to your main adm. account.

---

### Post by CalvinBaron on 2012-06-24
I can't stress enough how deeply I appreciate your effort to help me out with this.

I've followed your instructions and checked for updates using the "Update Manager" which shows me that there are currently no new updates available.

Would it perhaps be helpful if I filmed the "sequence of events" and posted a link to it here?

---

### Post by jmfal on 2012-06-24
You don't need to film any thing.
 The only thing I can think of right now is to restart and at the login screen click the gear at the top right, next to your name, and select switch users and se if you can login to your main account.

The thanks are appreciated!!

---

### Post by CalvinBaron on 2012-06-24
Done what you said, sadly that too didn't work.

I've already tried to access my original account in the console, and strangely that did work! That at least proves that the password is right and my account remains in some way accessible. 

Would it be possible to activate the Lubuntu desktop environment from the console once logged in to my original account?

I might add that this is actually the second time I am confronted with this particular problem, the first time, yesterday morning, I eventually re-installed the whole OS, but when *this* morning the same problem showed itself again I thought it better to ask for expert help.

---

### Post by steeldriver on 2012-06-24
If you can log in at the console (or virtual terminals Ctrl-Alt-F1...F6) then likely the issues is just that your xsession is failing to start

Sometimes this happens if you've been messing with starting X manually as root and your ~/.Xauthority and/or ~/.ICEauthority get owned by root - you can check that by logging in at the console or VT and then

```
ls -l ~/.*authority
```If that's the issue then you can 'sudo chown' or just 'sudo rm' either file (they will be regenerated when you successfully log in)

If that's *not* the issue then you will need to start poking around the greeter logs to see why the session manager is failing to authenticate you

---

### Post by jmfal on 2012-06-24
You can try to do that from the console , but I  don't know what you should try to do.

Did you try the Pscycocat link ??

You can use your original password it will just reset it.

I had the same thing happen to me a few years ago and I think I was OK till I used sudo and created some kind of security breach>>>>Had  to do a reinstall.

---

### Post by CalvinBaron on 2012-06-24
I'll give those things a try.

You'll hear the report.

Thank you both.

---

### Post by CalvinBaron on 2012-06-24
Thank you, **steeldriver**, for your support.

You should know that I belong to "Generation XP" and am used to a WYSIWYG kind of thing, so the task of having to enter commands looks rather daunting to me.

Yet I've done what you said and entered: ```
ls -l ~/.*authority
``` What then appeared was the following: ```
/home/calvin/.Xauthority
``` How to apply the 'sudo chown' command correctly? 

Remember, you're explaining this to a commandilliterate newbie that's very keen on learning but frightened by the prospect of accidentally making things worse.

---

### Post by steeldriver on 2012-06-24
did you include the "-l" on that command (that's "minus ell")? we are looking for who owns the files, it should be something like

```
 ls -l ~/.*authority
-rw------- 1 calvin calvin 10862 2012-06-20 10:32 /home/calvin /.ICEauthority
-rw------- 1 calvin calvin 49 2012-06-20 10:32 /home/calvin /.Xauthority
```If you see anything like "root root" instead of "calvin calvin" then that's something we can fix

---

### Post by CalvinBaron on 2012-06-24
You where right to point out the "minus ell" thing, I had misread "l" as the number one.

This time the result was indeed different and I hope correct.

Here it is: ```
-rw------- 1 calvin calvin 50 Jun 24 14:25 /home/calvin/.Xauthority
```

---

### Post by steeldriver on 2012-06-24
OK the good news is that looks OK... 

... which is also the bad news (i.e. the ownership of ~/.Xauthority is *not* what is stopping you from logging in)

not sure what to suggest next - what version of Lubuntu is it? what is your session manager?

```
cat /etc/X11/default-display-manager
```

---

### Post by CalvinBaron on 2012-06-24
It concerns the latest version of Lubuntu.

This code:

```
cat /etc/X11/default-display-manager
```

Elicited this response:

```
/usr/sbin/lightdm
```

UPDATE:
I've done some additional research and though I don't understand half of what I'm reading and the problem remains to be solved I do believe we are on the right track with this now.

Awaiting your response.

---

### Post by steeldriver on 2012-06-24
Well I really don't know what to suggest - I guess I would look in the lightdm log file(s) to see if there was anything suspicious, you could try 'grep'ing for your username, or the words 'auth/Auth' or 'WARNING' i.e.

```
sudo grep calvin /var/log/lightdm/*.log
sudo grep -i auth /var/log/lightdm/*.log
sudo grep WARNING /var/log/lightdm/*.log
```You could also try

```
tail ~/.xsession-errors
```to see if there's anything indicating your session started but then immediately terminated

---

### Post by jmfal on 2012-06-24
Try this if Steeldrivers commands don't fix it:

```
 sudo service lightdm start     
```

This should be done from recovery kernal, and select the shell 
and run command
and restart

---

### Post by steeldriver on 2012-06-24
^^^ so did I misunderstand the problem? I thought the lightdm greeter screen was coming up OK (e.g. the OP can log in with a guest account) - it's just he can't login at the greeter as 'calvin'

---

### Post by jmfal on 2012-06-24
**Re: Log-in trouble!**
 		^^^ so did I misunderstand the problem? I thought the lightdm greeter  screen was coming up OK (e.g. the OP can log in with a guest account) -  it's just he can't login at the greeter as 'calvin'

I'm not sure what happened, you should still check the log , maybe there is a clue hidden in there somewhere.

---

### Post by jmfal on 2012-06-24
Look at this link and set your password and auto login back to the way its supposed to be
copy and paste the   “gksu /usr/sbin/gdmsetup” command in a terminal and follow the links instructions to get you going and undo the autologin
If it wont take your password then you might have to do the pyscocat lilnk and reset your password

[http://www.thegeekstuff.com/2009/07/enable-automatic-login-in-ubuntu-kubuntu/](http://www.thegeekstuff.com/2009/07/enable-automatic-login-in-ubuntu-kubuntu/)

---

### Post by CalvinBaron on 2012-06-25
> I thought the lightdm greeter screen was coming up OK (e.g. the OP can log in with a guest account) - it's just he can't login at the greeter as 'calvin' This seems to be the case.


```
sudo service lightdm start
``` This I already attempted, but I'll try again today and this time "restart" as you recommended.


> [http://www.thegeekstuff.com/2009/07/...buntu-kubuntu/](http://www.thegeekstuff.com/2009/07/...buntu-kubuntu/) I'll be looking into this.


```
tail ~/.xsession-errors
``` I'll give this a try too, see what comes up.

UPDATE: Another problem presented itself, this time while making an attempt at the "automatic login" solution which **jmfal** suggested.

```
gksu /usr/sbin/gdmsetup
```

In order to run that function I need to perform administrative tasks, which of course requires a root password. Though I'm quite positive I got the password right (double checked it) it isn't accepted. This happens whenever (varying circumstances) I need to gain access to the root. I've tried both the password of my "calvin" account, the "new" account and the assumed to be correct password to the root. Should we see this as related to the first problem?

Thank you both.

You'll hear the report.

---

### Post by CalvinBaron on 2012-06-25
> **steeldriver said:**
> Well I really don't know what to suggest - I guess I would look in the lightdm log file(s) to see if there was anything suspicious, you could try 'grep'ing for your username, or the words 'auth/Auth' or 'WARNING' i.e.

```
sudo grep calvin /var/log/lightdm/*.log
sudo grep -i auth /var/log/lightdm/*.log
sudo grep WARNING /var/log/lightdm/*.log
```You could also try

```
tail ~/.xsession-errors
```to see if there's anything indicating your session started but then immediately terminated

Each time I enter a "sudo" command which of course requires a password a similar message is given in response: ```
password for newaccount: newaccount is not in the sudoers file. This incident will be reported.
``` I is confused utterly.

---

### Post by steeldriver on 2012-06-25
> **CalvinBaron said:**
> Each time I enter a "sudo" command which of course requires a password a similar message is given in response: ```
password for newaccount: newaccount is not in the sudoers file. This incident will be reported.
``` I is confused utterly.

Sorry I was assuming you would be doing this from a virtual terminal / console after logging in with your regular 'calvin' account (which *does* have sudo permissions I assume?)

If you want to fix everything from a *new* account you will need to give *that* account sudo permissions:

1. either switch to a VT and login there as 'calvin', or 'su calvin' in a GUI terminal

```
su calvin
```2. add 'newuser' to the sudo group

```
sudo adduser *newuser* sudo
```Let us know how it goes

---

### Post by CalvinBaron on 2012-06-25
Well, now that I've added *newuser* (from inside the VT) to the sudo group of *calvin* the following commands yield different responses.

FIRST:

```
 sudo service lightdm start
``` The above elicits this: ```
Job is already running: lightdm
```

Let's assume for a moment the problem is that "lightdm" simply doesn't start properly when at the greeter screen I log-in as *calvin*. (Who knows what I've done wrong?) Then, perhaps, I could try to log-in as *calvin* at the greeter screen by way of the console, instead of through the GUI terminal or VT of *newuser*, and once logged-in try to activate the GUI. - For that's basically the problem, I can log-in to my original *calvin* account through a GUI terminal once logged-in at another account, just not at the greeter screen.

Once more the sequence of events:

Computer started, begin of cycle: > greeter screen appears, 2 accounts + Guest are listed > select *calvin*, enter password > access granted > screen turns black > moment later greeter screen re-appears > select *calvin*, etc. etc. ad infinitum. 

And this problem exclusively affects the *calvin* account. Aside from that Lubuntu works fine, I'm currently working from the same machine but using the *newuser* account, which I created while logged-in to the Guest account.

SECOND:

```
tail ~/.xsession-errors
``` The response to the above:```
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

Thanks for staying involved in this increasingly frustrating matter.

---

### Post by steeldriver on 2012-06-25
hi can you please try the first group of commands? try to log in at the greeter screen as 'calvin' first so we make sure we catch the error

```

sudo grep calvin /var/log/lightdm/*.log 
sudo grep -i auth /var/log/lightdm/*.log 
sudo grep WARNING /var/log/lightdm/*.log

```

the xsession-errors are interesting but shouldn't stop you logging in, I don't think...

---

### Post by CalvinBaron on 2012-06-27
I've done what you said but it seems to no avail, the screen turned black not to return until after a reboot. 

Why this occurred will remain a question unsolved for now.

I'll be re-installing the system to get it working properly again.
But of course I can't afford to keep resorting to that solution, therefore this'll be the last time. 
Does Lubuntu fail beyond immediate repair again, then it's back to what I am used to. :-|

Thank you both very much for your support.

---

### Post by steeldriver on 2012-06-27
sorry we didn't manage to fix it :(

---

