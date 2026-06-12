---
title: "launch app on server via ssh"
date: 2009-08-03
forum: General Help
---

### Post by RAMDrive on 2009-08-03
I have 4 machines running 9.04 with SSH enabled.  There are times I need to start an application locally on one of the machines from a different machine, say via ssh.  Does anyone know how to do this?  All searches have failed me.


Thank you

---

### Post by wojox on 2009-08-03
What's the program?

---

### Post by Primefalcon on 2009-08-03
```
export DISPLAY=<remote_computer_ip>:0.0
```

that tells the computers to export all display to the remote machine, then just run your aps such as say gedit such and such and them go and look at the remote machine

---

### Post by RAMDrive on 2009-08-04
> **wojox said:**
> What's the program?

vuze.  I don't have it starting at login because I don't always need it.  However I do have it set to autostart torrents in a folder.  This allows me to sftp files to the folder and vuse will start downloading them if it's running.  So I need to know how to start vuze on the remote PC from another location.

Thanks

---

### Post by barnex on 2009-08-04
You can also use:
```
ssh -Y user@machine
```
This will forward X-connections to your local machine. Just type vuze after ssh'ing and the window will pop up on your local screen.

note: you might want to use the flag -C for compression as well.

---

### Post by Dr Small on 2009-08-04
I always use:
```
ssh -XC -c blowfish user@host
```

And then once connected, type the name of the GUI application that I want to be ported to my display over SSH.

---

### Post by Primefalcon on 2009-08-04
Oh I misunderstood my way will open the app visually on the remote machine, to open it locally just do a -X when you connect using ssh

---

### Post by RAMDrive on 2009-08-04
I thank everyone for their help, however I believe we might be misunderstanding each other.  

I need to log into the server from a remove PC and launch an application on the server then disconnect leaving the application running on the server.  I don't care about being able to see the launched application on the remote machine.

---

### Post by bodhi.zazen on 2009-08-04
> **RAMDrive said:**
> I thank everyone for their help, however I believe we might be misunderstanding each other.  

I need to log into the server from a remove PC and launch an application on the server then disconnect leaving the application running on the server.  I don't care about being able to see the launched application on the remote machine.

use screen ;)

ssh into the server , then launch a screen session.

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

either that or 

ssh user@server command
ssh user@server 'nohup command'
ssh user@server 'detach command'

or some variant depending of course on the command and if you wish to resume the session, in which case, go with screen

---

### Post by Glyndwr on 2009-08-04
> **RAMDrive said:**
> 
I need to log into the server from a remove PC and launch an application on the server then disconnect leaving the application running on the server.  I don't care about being able to see the launched application on the remote machine.

It sounds like you need nohup.

Try this:
ssh <server>
nohup <application> &
exit

---

