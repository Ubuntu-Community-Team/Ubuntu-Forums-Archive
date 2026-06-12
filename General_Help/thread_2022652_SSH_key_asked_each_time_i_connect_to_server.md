---
title: "SSH key asked each time i connect to server"
date: 2012-07-11
forum: General Help
---

### Post by biji on 2012-07-11
Now in precise (installed from scratch), ubuntu does not ask SSH password in X window. and ssh password asked each time i want to connect, previously it can be saved

Im using unity desktop

Please guide 
thanks

---

### Post by JKyleOKC on 2012-07-11
The most secure solution is not to save the password, but instead to configure your ssh connection to use RSA keys instead. After months of dealing with the password-every-time problem, yesterday I changed my configuration over and now it just works when I connect.

To create the key, first at your local machine run ```
ssh-keygen -t rsa
``` which will create the hidden directory ".ssh" in your home directory if it does not already exist, and will then create two files in that directory: "id_rsa" and "id_rsa.pub" which are the private and public keys just generated. When the ssh-keygen program asks you to enter a pass-phrase just hit Enter and then Enter again when it asks you to repeat; if you do tell it anything here it will ask for that pass-phrase every time you connect, defeating your purpose!

Check the properties of both files to make sure that "id_rsa" is readable only by its owner, you, while "id_rsa.pub" can be read by anyone.

Next, log into your remote machine via ssh and copy the content of your "id_rsa.pub" file onto the end of the remote's "~/.ssh/authorized_keys" file. If that file does not exist, you can create it with ```
touch ~/.ssh/authorized_keys
``` at the remote end. I did the copy through the ssh session by typing ```
cat 192.168.0.2:~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
``` where the "192.168.0.2" was the LAN address of my local machine, but you can use any other technique that works. Just be sure that the data is copied while any existing data remains undisturbed.

Finally, close the ssh session with ```
exit
``` and try to open a new ssh session. You may get a dialog asking you to verify that you want to connect, this first time; it won't happen on later connections. If it opens without asking for a password you are almost done; what remains is to modify the "/etc/ssh/sshd_config" file on the remote machine to turn OFF its request for a password. This isn't absolutely necessary but will improve security; if you want step-by-step instructions let me know but at this point I think you will find that your immediate question is answered.

---

### Post by biji on 2012-07-11
THanks a lot for reply.
but the problem is not setting up the key. :popcorn:
the password, i mean the passphrase is asked each time i want to connect:
Enter passphrase for key '/home/biji/.ssh/id_dsa': 

it is written on terminal. usually pop-up a dialog asking for password and ask if i want to save it

where could be wrong.. or maybe reinstall some package?

---

### Post by QIII on 2012-07-11
When you were generating your keys, was there a prompt to enter a passphrase?

---

### Post by JKyleOKC on 2012-07-11
The problem is that you (or someone) **DID** enter a pass-phrase when running ssh-keygen to create the keys. That forces the program to ask for it each time you connect.

You might be able to fix it by (1) renaming the .ssh directory on the local machine to .ssh-saved and renaming the authorized_keys file on the remote machine to authorized_keys-old, then (2) going through the keygen steps I described in my previous message, taking care **NOT** to enter a pass-phrase. If this works, you can then delete the renamed files.

However it's possible that when you rename the remote file via ssh, the program might disconnect you and prevent you from getting back in via ssh, so be sure you have direct access to the remote machine just in case something goes wrong...

---

### Post by TrombaMarina on 2012-09-24
I just typed ssh-add at the command line and entered my passphrase and I was good (even after closing that terminal window and opening another).  I imagine it will need my pass-phrase again after I reboot or maybe log out.  That might be the most secure thing to do because you aren't running ssh-agent (which allows access to your private key) until you actually need it that day.

For longer automatic access to your private key, you might try typing "Passwords and Keys" into the search box into the Dash in the upper-left corner of the Unity screen.  Under the "My Personal keys" tab, click on an entry and it should say "Type: Secure Shell Key."  Presumably this is how gnome-keyring accesses ssh-agent, or maybe some kind of ssh-agent replacement that's now part of gnome-keyring.  You might try fooling around with that to nudge it into remembering how to unlock your private key in the future.

---

