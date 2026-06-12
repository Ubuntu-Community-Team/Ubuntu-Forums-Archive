---
title: "Login Error - Please Help Ubuntu Noob!"
date: 2010-05-26
forum: General Help
---

### Post by JRummy16 on 2010-05-26
I am very new at Ubuntu so be gentle :) 
 
I installed ubuntu on my 64-bit system using wubi and everything was running smooth for a while. I have been compiling builds from aosp. I logged in and out successfully on several occasions but not the system won't let me login.
 
I know it isn't my password. When I go to login it continues as normal, then flashes a screen so fast I haven't been able to read it. I have gone into terminal by holding ctrl, alt, f4 and when I login there I notice the following possible errors that could be my issue:
 
-bash /home/myusername/.profile: line 24: unexpected EOF while looking for matching ''''
-bash /home/myusername/.profile: line 27: sytax error: unexpected end of line
 
Pretty **please **help a noob out! I have some information on my system I don't want to loose. I have done a search and tried different solutions w/ no luck.

---

### Post by sylvester_0 on 2010-05-26
I'd recommend you move your old profile aside and start over.

```
sudo mv /home/username /home/usernameold
sudo mkdir /home/username
sudo chown username /home/username
```

Then try logging in again.

---

### Post by Serpher on 2010-05-26
Have you activated the root account by ever typing in the command:

```
sudo passwd
```


If so log onto your root account (User: root Pass: Whatever you set it to using that command) then run:

```
passwd (LoginName)
```

---

