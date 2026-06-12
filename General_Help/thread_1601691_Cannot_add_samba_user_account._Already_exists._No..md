---
title: "Cannot add samba user account. Already exists. No. It doesn't."
date: 2010-10-20
forum: General Help
---

### Post by Roasted on 2010-10-20
I tried to add a samba user account on an Ubuntu machine called "video" like I had on another Ubuntu machine, but it's telling me it already exists. At one point I had added the user via terminal, but the user did not show up in system-config-samba (the popular samba gui a lot of people use). So now I'm trying to re-add him and it's not working. Likewise, if I use terminal to sudo smbpasswd -x video, it says failed to find an entry for that user.

As far as I can tell, the user doesn't exist - yet I can't add him because it "already exists."

Ideas?

---

### Post by Roasted on 2010-10-21
:(:(:(

---

### Post by sikander3786 on 2010-10-21
Can you try to add it simply by **useradd video** and see if it exists there?

---

### Post by endotherm on 2010-10-21
so what command is failing? smbpasswd?
if you have not run smbpasswd but you have a unix user, just run this line:
```

sudo smbpasswd -a <username>

```and set a password when prompted. 

I believe that the user exists as a unix user but not a samba user. can't quite tell from the description however. you can confirm whether a unix user exists from the output of 
```
cat /etc/passwd
```

does system-config-samba actually work? every frontend for samba I've tried has been rather problematic.

---

### Post by Morbius1 on 2010-10-21
As a follow-up to endotherm's post you might also want to look at the samba password file:
```
sudo pdbedit -w -L
```You'll get some crazy looking output like this:
> nobody:65534:XX...:XXX:**[COLOR=Blue][U          ][/COLOR]**:LCT-00000000:The **[COLOR=Blue][U          ] [/COLOR]**[COLOR=Blue][COLOR=Black]tells you it's state[/COLOR][/COLOR][COLOR=Blue]:

[COLOR=Black]U - Regular active user
DU - disabled user

Even if the samba user was disabled a "smbpasswd -x" should have removed it though so I'm a little mystified by the problem. 

[/COLOR][/COLOR][B][COLOR=Blue][COLOR=Black]
[/COLOR]
[/COLOR][/B]

---

### Post by Roasted on 2010-10-22
What was failing was in the system-config-samba GUI when I tried to add the user "video." The terminal commands never yielded an error, except smbpasswd -x video yielding "no user exists" or whatever. I'm assuming that between me using terminal + the config GUI that that's where it got tripped up. But I'm still confused over why it would be a... problem...

---

### Post by endotherm on 2010-10-22
> **Roasted said:**
> What was failing was in the system-config-samba GUI when I tried to add the user "video." The terminal commands never yielded an error, except smbpasswd -x video yielding "no user exists" or whatever. I'm assuming that between me using terminal + the config GUI that that's where it got tripped up. But I'm still confused over why it would be a... problem...

Ah ha! i think the issue may be the username "video". Video is a default usergroup in ubuntu, and that prevents you from creating a standard unix user with that name. part of the user creation process is to create a group that uses the same name as the user, but this would fail in your case, since Video the group already exists.

try using a differant username (perhaps 'vidUser' or somesuch) and see if you don't have better results.

---

### Post by Roasted on 2010-10-22
> **endotherm said:**
> Ah ha! i think the issue may be the username "video". Video is a default usergroup in ubuntu, and that prevents you from creating a standard unix user with that name. part of the user creation process is to create a group that uses the same name as the user, but this would fail in your case, since Video the group already exists.

try using a differant username (perhaps 'vidUser' or somesuch) and see if you don't have better results.

You would think that. As part of the initial Ubuntu install, creating a user Video failed. Once I got the installation going with another username, I tried to add "Video" as a local user again once the installation was completed - guess what? It worked.

Ahh yes...

---

