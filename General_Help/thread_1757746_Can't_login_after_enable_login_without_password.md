---
title: "Can't login after enable login without password"
date: 2011-05-13
forum: General Help
---

### Post by peacebreaker on 2011-05-13
So I have enabled login without password - but now, whenever i click my username to login after restart, it displays few error messages:

Could not update ICEauthority file /home/username/.ICEauthority

There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following required folders: /home/username/Desktop, /home/username/.nautilus.

which i think the system trying to access my home directory, which encrypted. If i understand the process correctly, the home directory would need my passphrase(/password?) to decrypt/open my home directory, correct? But then there is not passphrase given to it so it can't decrypt/open my home dir.

Now my desktop is empty without anything on it, although i can still access Terminal via Ctrl-Alt-t. If I access my home dir via this, it is still encrypted, and I have to run command ecryptfs-mount-private, and give it my login passphrase, to open it.

What can i do to fix this?

---

### Post by peacebreaker on 2011-05-13
Any idea peeps?

Should i decrypt my home directory first?

[http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst)

?

---

### Post by arvizard on 2011-05-19
I had the same problem today and here is how I fixed it.
1. Log in to the account.
2. Press Ctrl + Alt + T to open the terminal.
3. create a new user by typing 'sudo adduser username'
4. Enter details asked.
5. Once the user is created, you can restart the system and log in using the new ID.
Then, just goto the users and groups setting and make the required changes to enable password on login.
Things should be back to normal.

---

### Post by mkyweriga on 2011-05-28
Thank you for your post. I just had the same problem and your solution worked. 
But, do I have to enter a password at login? That seems dumb. My computer is at home and my roommates are free to use it. I guess I'll just have a super simple password, but I'd rather have none at all. Any suggestions?

I am running 11.04 or an older Dell laptop (Latitude D630, intel core2 duo)

Thanks! :)

---

### Post by wildmanne39 on 2011-05-28
> **mkyweriga said:**
> Thank you for your post. I just had the same problem and your solution worked. 
But, do I have to enter a password at login? That seems dumb. My computer is at home and my roommates are free to use it. I guess I'll just have a super simple password, but I'd rather have none at all. Any suggestions?

I am running 11.04 or an older Dell laptop (Latitude D630, intel core2 duo)

Thanks! :)
Hi, I think if you enter nothing then it will work without a password.

---

### Post by wildmanne39 on 2011-05-28
> **peacebreaker said:**
> So I have enabled login without password - but now, whenever i click my username to login after restart, it displays few error messages:

Could not update ICEauthority file /home/username/.ICEauthority

There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following required folders: /home/username/Desktop, /home/username/.nautilus.

which i think the system trying to access my home directory, which encrypted. If i understand the process correctly, the home directory would need my passphrase(/password?) to decrypt/open my home directory, correct? But then there is not passphrase given to it so it can't decrypt/open my home dir.

Now my desktop is empty without anything on it, although i can still access Terminal via Ctrl-Alt-t. If I access my home dir via this, it is still encrypted, and I have to run command ecryptfs-mount-private, and give it my login passphrase, to open it.

What can i do to fix this?
Hi, also there is a link for resetting passwords if it comes to that. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by The.Red.Pill on 2011-11-24
I had this very same issue and found this fix which also works - it will grant you access back to your folders and system etc where you can undo the changes you made in user accounts which caused the issue in the first place!

To fix just open the terminal and type this: 

chmod 755 /home/x

where x is your username, then restart :)

[http://thingsyoudontlearnatschool.blogspot.com/2011/01/fixing-there-is-problem-with.html]("http://thingsyoudontlearnatschool.blogspot.com/2011/01/fixing-there-is-problem-with.html")

---

