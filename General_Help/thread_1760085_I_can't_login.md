---
title: "I can't login"
date: 2011-05-16
forum: General Help
---

### Post by Mina Fouad on 2011-05-16
Hi all, 
I've a problem with my ubuntu 10.04 suddenly when I opened my laptop and after I've entered my password then I redirected _**to a black screen and then to **_the same screen again and so on what I can do

---

### Post by aysiu on 2011-05-16
> **Mina Fouad said:**
> Hi all, 
I've a problem with my ubuntu 10.04 suddenly when I opened my laptop and after I've entered my password then I redirected to the same screen again and so on what I can do
That's weird.

You can reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Mina Fouad on 2011-05-16
firstly thanks for your help... but of course this is not my problem I was redirected to a black screen then to the screen to enter my password again.. and I already have another account (oracle) with no password also have the same problem..
last time I shut down my laptop I've uninstalled Oracle Database 10g .. may this information is valuable..

---

### Post by Mina Fouad on 2011-05-16
I need urgent help

---

### Post by StrayEddy on 2011-05-16
Can you type a command? If that s the case try to type "gdm" or "startx"
 
Try Ctrl+Alt+F1 to open a terminal, then type the commands.
 
If anything prompts or changes, post it here.

---

### Post by Mina Fouad on 2011-05-16
thanks for your help but fatal error appears with startx and nothing changed :(

---

### Post by StrayEddy on 2011-05-16
Post your error, we ll take a look.

---

### Post by Mina Fouad on 2011-05-16
I think the problem caused because in last time I removed oracle DBMS Now When I login through the terminal I found this error:
  
> 
-bash /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle-env.sh :No such file or directoryif I run gdm:
> .:29: can't open /usr/lib/.../oracle-env.sh   //the same path as aboveif I run startx:

> server is already active for display 0
if this server is no longer running, remove 

 /tmp/.x0-lock
please consult the x.Org foundation 

ddsigGiveUp: closing log
Invalid MIT-MAGIC-COOKIE-1 keygiven up
xinit: Resource temporarily unavailable (errno 11) unable to connect to x server
 
xinit: no such process (errno 3) :Server err

---

### Post by aysiu on 2011-05-16
I would honestly try a reboot, but if that still doesn't work, log in and try ```
sudo service gdm stop
sudo service gdm start
```

---

### Post by Mina Fouad on 2011-05-16
> **aysiu said:**
> I would honestly try a reboot, but if that still doesn't work, log in and try ```
sudo service gdm stop
sudo service gdm start
```

Nothing happened :( I think the problem related to

> -bash /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle-env.sh :No such file or directory

---

### Post by aysiu on 2011-05-16
Try this command. ```
nano ~/.bashrc
``` That should open your bash preferences file in a text editor. See if you can find what's referencing Oracle and comment out the line (*comment out* means put a *#* at the beginning of th eline).

---

### Post by Mina Fouad on 2011-05-16
> **aysiu said:**
> Try this command. ```
nano ~/.bashrc
``` That should open your bash preferences file in a text editor. See if you can find what's referencing Oracle and comment out the line (*comment out* means put a *#* at the beginning of th eline).

I remembered that when I installed the oracle 10g I've added those line :

```
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
```
[U][B]and I made them comments 
[/B][/U]

but nothing also :( :(

---

### Post by Mina Fouad on 2011-05-17
really I need urgent help

---

### Post by satish_j on 2011-05-17
I think you removed some system files along with uninstalling oracle.I recently faced the similar problem after uninstalling Pulseaudio.
Did you _completely uninstall_ oracle from synaptic?
You will have to boot to recovery mode and install those packages again which got removed with Oracle.

---

### Post by Mina Fouad on 2011-05-17
> **satish_j said:**
> I think you removed some system files along with uninstalling oracle.I recently faced the similar problem after uninstalling Pulseaudio.
Did you _completely uninstall_ oracle from synaptic?
You will have to boot to recovery mode and install those packages again which got removed with Oracle.

yes,
but I think my problem comes from: 

```
-bash /path to oracle/oracle_env.sh :No such file or directory 
```

How can I fix this error which appears each time I login through the terminal

---

### Post by Mina Fouad on 2011-05-17
Also, 
I modified my PATH with:
> 
[COLOR=Red][COLOR=Black]ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server 
export ORACLE_HOME 

ORACLE_SID=XE 

export ORACLE_SID

NLS_LANG=[/COLOR][/COLOR]`$ORACLE_HOME/bin/nls_lang.sh` 

export NLS_LANG 
[COLOR=Black][/COLOR][COLOR=Red][COLOR=Black]
PATH=$ORACLE_HOME/bin:$PAT[/COLOR][FONT=monospace][COLOR=Black]H 

export PATH[/COLOR][/FONT]
[/COLOR]



---

### Post by satish_j on 2011-05-17
If you completely removed oracle,then the Oracle Path variables should not be the reason for your system not booting up.
Can you boot to recovery mode and switch on the Internet from it?

---

### Post by Mina Fouad on 2011-05-17
I can't use the Internet directly BUT I should enter a user name and password 
Is there a way to open a browser through the terminal ??

---

### Post by satish_j on 2011-05-17
Do you use an GUI to start Internet in normal desktop login.If yes,then iam afraid you need to find some terminal approach to start the Internet from Recovery mode.
Internet is required since packages needs to be installed again.If you cannot find any terminal-based approach to start the internet,then you nay need to re-install OS.

---

### Post by Mina Fouad on 2011-05-17
I tried and connected to the Internet and from the recovery I've run dpkg to repair the packages but nothing happened :((

---

### Post by StrayEddy on 2011-05-17
Ok,. if the file oracle/oracle_env.sh is missing,
 
maybe you should try to create it, just to overcome this problem (not solve it)
 
To create the file, go in the oracle folder:
use "cd"
and then create the file: 
"touch oracle_env.sh"
Finally type: 
"sudo chmod +x oracle_env.sh" to make the script executable.
 
Then reboot to see if you got another error.
 
Maybe it will give you another error, cause what i am suggesting is not a way to solve the problem, but for you to be able to login.

---

### Post by Mina Fouad on 2011-05-23
sorry, the same problem exists, 
I want to say something may be valuable I followed this link to install oracle 10g 
[http://dohaesam.blogspot.com/2011/03/upgrade-to-apex-40.html](http://dohaesam.blogspot.com/2011/03/upgrade-to-apex-40.html)

---

### Post by satish_j on 2011-05-24
ok,boot into recovery console and run foll(first run commands to start the internet,if any)
```

sudo apt-get install gnome-applets indicator-me indicator-applet-session indicator-applet gnome-session gnome-panel gnome-control-center gnome-media gnome-orca gnome-settings-daemon libmlt++-dev libmlt++3 libmlt-dev

```
after above packages are installed successfully,run
```

sudo reboot

```
You should get to the login screen.
Best of Luck...

---

### Post by Mina Fouad on 2011-05-24
> **StrayEddy said:**
> Ok,. if the file oracle/oracle_env.sh is missing,
 
maybe you should try to create it, just to overcome this problem (not solve it)
 
To create the file, go in the oracle folder:
use "cd"
and then create the file: 
"touch oracle_env.sh"
Finally type: 
"sudo chmod +x oracle_env.sh" to make the script executable.
 
Then reboot to see if you got another error.
 
Maybe it will give you another error, cause what i am suggesting is not a way to solve the problem, but for you to be able to login.

sorry, I created it wrongly. but now it works :) thanks a lot

---

### Post by Mina Fouad on 2011-05-24
> **satish_j said:**
> ok,boot into recovery console and run foll(first run commands to start the internet,if any)
```

sudo apt-get install gnome-applets indicator-me indicator-applet-session indicator-applet gnome-session gnome-panel gnome-control-center gnome-media gnome-orca gnome-settings-daemon libmlt++-dev libmlt++3 libmlt-dev

```
after above packages are installed successfully,run
```

sudo reboot

```
You should get to the login screen.
Best of Luck...

thanks also :)

---

