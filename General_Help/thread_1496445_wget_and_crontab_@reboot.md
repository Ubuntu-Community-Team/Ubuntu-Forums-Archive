---
title: "wget and crontab @reboot"
date: 2010-05-29
forum: General Help
---

### Post by bubaliba on 2010-05-29
Goal: run wget shell script at startup.

I want my computer to automatically download a file using wget at startup.
I wrote a shell script and scheduled it in crontab.

**downloader.sh**
```
#Download file.txt
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt
#Create log
echo "$(date) - Ran update." >> ~/Downloads/file.log
```

Everything is OK when I run it myself.
Crontab fails to download the file, it only creates an empty file.txt and a correct file.log.

**crontab -l:**

```
@reboot /home/downloader.sh
```

Edit: My assumption is that the script runs before the computer establishes the wireless connection. Thoughts?

---

### Post by DagMan on 2010-05-29
crontab is really picky about having any output.  It will usually fail if there is any so anything that you aren't directing into a log file is best sent to /dev/null.  wget typically updates the file progress in the terminal, and that info should be redirected into /dev/null

```
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt >/dev/null
```

and you may as well add something in case it still fails, then you can look at why.

```
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt >/dev/null 2>>/why/did/I/fail
```

Its also, however, quite possible that its simply running before your networking has finished starting.  The log file in the second code block would suggest if that was the case.  You could put a sleep command in the script, or if the permissions are okay and you're using a desktop rather than a server you can add it to the startup scripts in the menu, which also might require a little bit of sleep before it fetched the file.

---

### Post by bubaliba on 2010-05-29
Thank you very much. I had doubts if the whole situation isn't caused by the fact that the script runs before I'm connected to the Internet, so I decided to add it to the startup programs (i.e. ~/.kde/Autostart/script.desktop). It works for now (although it's more of a roulette), but I'll try to think of a more elegant solution.

How can I 'sleep' the script?

PS

```
--2010-05-29 21:40:09--  http://website.com/file.txt
Resolving website.com... failed: Name or service not known.
wget: unable to resolve host address `website.com'
```

So I guess Autostart doesn't really help. How can I delay the script? It would be great if I could delay it not in seconds/minutes but e.g. when an Internet connection is established.

---

### Post by DagMan on 2010-05-30
sleep is called by seconds by default.  You can make it use hours minutes or days instead.

sleep 3d
would make the script just sit there for 3 days and then it would move to the next line in the script.
sleep 3 
would make it sit there for 3 seconds and then move to the next line.

This will still be hit and miss if you're networking doesn't connect properly every time, but you'd add the sleep command above the other ones in the same script.

```
#!/bin/bash

#tell the script to do nothing for the next 25 seconds, and then move on to the next command
sleep 25

#Download file.txt
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt

#Create log
echo "$(date) - Ran update." >> ~/Downloads/file.log
```

you might also want to have it instead ping the website that you're wanting to download the file from so you ensure there's a connection.  There's much better ways of doing it I'm sure.

```
#!/bin/bash

#set x equal to anything that is not zero
#in the loop it will be set to the exit code of the ping command
#and will tell us if ping has exited as successful or not.
x="awesome"

#set y equal to zero.  It will serve as a counter and the loop will
#increase it by one every time it goes through
y="0"

#make loop that moves forward and on to wget once it successfully pings 
#the hosting website so we know there's a network connection
#and if it fails to do so within 30 seconds (3 second sleep command * y incrementing to 10) 
#then we exit the script entirely
while [ "$x" != "0" ] ; do
    if [ "$y" = "10" ] ; then
      exit
    fi
  sleep 3
  let y=y+1
  ping -c 1 website.com
  x=$?
done

#Download file.txt
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt

#Create log
echo "$(date) - Ran update." >> ~/Downloads/file.log
```

I haven't tested this so you'de need to give it a test run yourself.  Also, if you wanted to, you could add 
echo "$(date) - failed" >> /Downloads/file.log
before the exit command and after this part  
if [ "$y" = "10" ] ; then

note that the ping command only tries one ping each time, and that you ping the website and not website/file.txt or http:/website.com but just website.com
You could just as easily ping google.com, or your own ISP  since you're looking for the internet to be accessable and the site may be down.  Also, you could just redirect error messages from wget into the log file as well to see if an error was the result of the site you wanted being down.
```
wget -c -r --retry-connrefused --user-agent="autodownloader" http://www.website.com/file.txt -O ~/Downloads/file.txt  2>> /Downloads/file.log
```

---

### Post by bubaliba on 2010-05-30
Thank you very much!
I'm treating writing the script as an educational opportunity and you helped me a lot.

As for autostart, I'm going to read up on rc.d services because I heard that they are present in all Linux distributions and I'd love to be able to share this tiny script with others.

---

