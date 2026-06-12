---
title: "SSH Script writing"
date: 2010-11-14
forum: General Help
---

### Post by alibahaloo on 2010-11-14
Hello everyone, i need some help in writing a script
I've written the following small script to turn on my server which is on my local network:
```
#!/bin/bash
# init
function pause(){
   read -p &#8220;$*&#8221;
}
echo "Starting up Dell.."
echo "------------------------------------------------------------------------"
wakeonlan 00:15:c5:56:a0:fd
echo "------------------------------------------------------------------------"
echo "Successful...Dell Started"
pause 'EOF'
exit
```

with this script i can turn on the system sucessfully, in the other hand i wish to turn off the device via network too, so i use SSH, and send the following command to turn it off:
```
ssh user@ipaddress
password for user
sudo shutdown -h 0

```

i wish to have this command as a script, in other words, i want a script to carry on these function. I've written the following script; it connects to the server and asks for the password, but after that it doesn't continue to carry on the commands. i guess writing scripts for ssh is different.
this is the script:
```
#!/bin/bash
# init
function pause(){
   read -p &#8220;$*&#8221;
}
echo "Sending Shutdown command to server..."
echo "-----------------------------------"
ssh user@ipaddress
echo "Connected to server"
echo "Sending shutdown command..."
sudo shutdown -h 0
pause 'OK'
exit
```

how should i do this? if anyone knows the way, please let me know

thanking you in advance

cheers

---

### Post by Monotoko on 2010-11-14
You will need to generate an SSH key, so that the computers can "talk" without a password.

[http://e-articles.info/e/a/title/How-to-Generate-a-Key-Pair-Using-OpenSSH/](http://e-articles.info/e/a/title/How-to-Generate-a-Key-Pair-Using-OpenSSH/)

also, in order to send commands:
```
ssh user@systemip 'command here'
```

will generally give you an output and run the command, if you are trying to run multiple commands use ; so:

```
ssh user@systemip 'command1; command2; command3'
```

---

### Post by SeijiSensei on 2010-11-14
You need to [set up RSA authentication]("http://news.softpedia.com/news/How-to-Use-RSA-Key-for-SSH-Authentication-38599.shtml") which uses predefined keys.  Then you can run commands with SSH and not have to enter a password.

---

