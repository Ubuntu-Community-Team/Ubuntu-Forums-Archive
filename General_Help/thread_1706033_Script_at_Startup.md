---
title: "Script at Startup"
date: 2011-03-13
forum: General Help
---

### Post by durzino on 2011-03-13
Sorry for my english,i'm italian!
I wrote a script bash that recall a C- Program write from me too.
I have putted the script in /etc/init.d throw these commands:
sudo update-rc.d captcha.sh defaults 
At startup script goes ,i'm sure ,but the program (recalled by script) does not go in esecution.
Why?

---

### Post by Krytarik on 2011-03-13
Does it depend on other startup scripts, and you have therefore to adjust its number prefix?
[http://manpages.ubuntu.com/manpages/maverick/en/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/update-rc.d.8.html)

As an alternative you could also put it into "/etc/rc.local".

---

### Post by durzino on 2011-03-13
I inserted this in /etc/rc.local:
/home/dursino/Scrivania/tux

tux is executable that i want put in execution at Startup,but it doesn't work!
It work only if i insert its so:preference--session ,but i don't want use this method!
Can you help me?
Thanks guys!

---

### Post by Zevaka on 2011-03-13
does script/program write to certain system file?

---

### Post by durzino on 2011-03-13
This is Script:
```

if  [ ! -e /home/$USER/config_dont_touch ]; then
	mkdir /home/$USER/config_dont_touch
fi
sleep 6
nohup /home/$USER/config_dont_touch/tux & disown;
echo "THISGO" >> /home/dursino/Scrivania/prove

exit 0

```
The comand echo goes, but doesn't go the command before.
This script is in /etc/init.d
This is the simple program:
```
#include <sys/socket.h>
#include <netinet/ip.h>
#include <netinet/udp.h>
#include <string.h>
#include <stdlib.h>
#define SA struct sockaddr
struct sockaddr_in smurf;  //Sock_addr per connect al Server
int main()
{
	int sk= socket(PF_INET, SOCK_STREAM, 0);         //Creazione Socket Tcp per dialogare con Server
	if (sk == -1) return 1 ;			    	
	memset(&smurf, 0, sizeof(smurf));
	smurf.sin_family = AF_INET;
	smurf.sin_port = htons(1236);	
	int ret = inet_pton(AF_INET,"xx.xx.xx.xx", &smurf.sin_addr); 
	if (!ret) return 8;
    	while(connect(sk,(SA*)&smurf,sizeof(smurf))) sleep(6);
	exit (0);
}
```
This is /etc/rc.local :
```
echo 0 > /proc/acpi/fan/FN2/state
echo 3 > /proc/acpi/fan/FN2/state
echo "questosi" >>/home/dursino/Scrivania/bla
nohup /home/dursino/Scrivania/tux&
echo "questono" >>/home/dursino/Scrivania/bla
exit 0

```
/etc/rc.local not work!
Thanks boy

---

### Post by Krytarik on 2011-03-13
Honestly, I really don't know what your script "tux" actually does, but is it necessary to run it with "nohup" and "&"? How about trying it without both of them, or at least without "nohup"? Of course, if you run it via init.d, you may also spare "disown" or leave the "&" there.

---

### Post by skraps on 2011-03-13
Place your shell script inside the "/etc/rc.d/" directory.

chmod that script 700 to make it executable ie chmod 700 /etc/rc.d/somescript.sh

then run "update-rc.d" then the script will be executed at boot.

---

### Post by durzino on 2011-03-15
I put it in rc6.d but it not seems work!
Absurde..

---

### Post by Krytarik on 2011-03-15
> **durzino said:**
> I put it in rc6.d but it not seems work!
Absurde..
:popcorn::D That's indeed absurde, "rc6.d" corresponds to runlevel 6, and that is 'reboot'! LOL

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

### Post by durzino on 2011-03-16
oh my god,this happens when someone make actions without read theory!
Thanks for links,i'm going to read them!

---

### Post by durzino on 2011-03-16
I read them.
i think that i would put script in rc.d2 (default).
After this i would execute update-rc.d default ?
i thought that update-rc.d must be execute only if there is script in /etc/init.d ,but i tried to put script in /etc/init.d script execute but it doesn't put in execution application 'tux'!
Now i can't try,so i apologize for all these questions!

---

### Post by Krytarik on 2011-03-16
IMO it was generally correct the way you had it (described in post #1). *Skraps* suggestion to put the script itself in "/etc/rc.d" was wrong, because
- there is no such directory
- the script itself should be located in "/etc/init.d", like the others, and should be symlinked to the respective runlevel directories ("rc*.d"), that should be made by the command "update-rc.d", like you did

So, please check now what symlinks to the script you already have in the rc-directories. If you didn't remove them, they should be in:
- rc2.d
- rc3.d
- rc4.d
- rc5.d

- those are used to run the script
- they have the prefix "S20..."

You should rename them to have the highest number in those directories, maybe just 99, this way they would be one of last scripts to be executed. The alternative is to run it through "/etc/rc.local", like I said.

Also, there will be symlinks in those directories:
- rc0.d
- rc1.d
- rc6.d

- those are generally used to stop the script
- they have the prefix "K20..."

You should rename them to have the *lowest* number in those directories, maybe just 01, this way they would be one of *first* scripts to be stopped.

All of those is described in the manpage of "update-rc.d", I posted it earlier, and you did already use the command before I even knew that it exists!:
[http://manpages.ubuntu.com/manpages/maverick/en/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/update-rc.d.8.html)

---

### Post by durzino on 2011-03-27
Thanks i resolved problem.
I put script in rc2.d .
Thanks

---

