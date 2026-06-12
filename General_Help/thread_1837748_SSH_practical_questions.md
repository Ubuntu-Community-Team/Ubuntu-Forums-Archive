---
title: "SSH practical questions"
date: 2011-09-02
forum: General Help
---

### Post by thunderbirdje on 2011-09-02
Hi everyone,

I have managed to set up SSH on my computer and can SSH into my computer within my LAN network.

1) I am wondering how I can reach my SSH server computer from outside my LAN? I looked up my external IP with [http://whatismyipaddress.com](http://whatismyipaddress.com) but did not succeed to connect. I also tried my hostname ip000.dyn0.gkk0.someprovider.net which also failed. It is ok for me to look up every time my probably different IP. I am not looking for a constant address to reach my dynamic IP SSH server computer because I will only use it from time to time.

2) In Gnome there is an option **Places > Connect to server... >** Wherre you can choose Service Type SSH which works with my LAN IP. When I let my friend connect to my computer in the same way, will the files being shared secured by the SSH protocol? And more important if he or I copy some files with the use of Nautilus, will these also go through the SSH tunnel? I just gave my friend Ubuntu and want to avoid a lot of stress using the shell.

3) When generating the keys, it is said that I should copy the public key to the SSH server computer. I managed that but I am wondering, is it so that everyone who generates a key can actually scp those key to my SSH server computer when they know the hostname (and or user) and thereby accessing my SSH server computer? Wondering about the safety...

Thank you for reading my long post!

---

### Post by mbuell on 2011-09-02
1. I recommend you google this - yesterday I was researching an ssh error, and saw a number of pages explaining methods of doing this. You do not tell us how your LAN is set up - so there are a number of hardware possibilities that could affect the answer. For instance, just assuming you have a home lan with a router, you will need to set the router to forward connections to your target ssh server. 

2. Yes, if Nautilus sets the connection using ssh, all the Nautilus traffic then uses that ssh tunnel for file transfers, etc.

---

### Post by mikejonesey on 2011-09-02
ssh keys are the most secure way to interact with a server remotley, scp would require a username and password to copy the key to your server, you can however disable passwords so only existing keys can login...

the only way this becomes a vulnerability is when you do something silly like run a tomcat servlet with vulnerable code as root... (then anyone has root priv to create keys)...

---

### Post by gdonwallace on 2011-09-02
You might check to ensure that port 22 is open on the external IP.  By default SSH uses port 22.  You also will want to ensure that the port mapping is set up to redirect that external IP to the internal IP.  

Each person that connects to that server via SSH will have a key generated.  Its part of the validation process that SSH uses to ensure that only "allowed" users are connecting to that machine.  

scp is part of the overall SSH program.  Like SSH (Secure shell) SCP is (secure copy) that uses SSH to copy files from one machine to another.  It uses the key generated from SSH to validate the connection between machines and performs the same validation before allowing the copy to happen.

Check this URL out for additional information about SSH, it has helped me alot:
[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

---

### Post by thunderbirdje on 2011-09-02
Indeed, I had to forward my port in my router, that solved the problem!

Thank you all for helping me out!

> **gdonwallace said:**
> 
Check this URL out for additional information about SSH, it has helped me alot:
[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

This was very helpful as well!

Happy and enjoying SSH

---

### Post by gdonwallace on 2011-09-02
Glad you where able to get it fixed.

SSH / SCP saved me a lot of time getting files moved around to different servers.

---

