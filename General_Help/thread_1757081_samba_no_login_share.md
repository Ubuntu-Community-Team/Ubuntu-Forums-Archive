---
title: "samba no login share"
date: 2011-05-13
forum: General Help
---

### Post by Whiteice on 2011-05-13
I have a issue with samba share. I would like to share this directory with the need to login kinda like a drop box. Any suggestions heres my conf for it

[storage]
comment = General Storage
path = /home/stizzle/Storage
guest ok = yes
browsable = yes
writable = yes
security = share
public = yes

---

### Post by bobwyajnr on 2011-05-13
> **Whiteice said:**
> I have a issue with samba share. I would like to share this directory with the need to login kinda like a drop box. Any suggestions heres my conf for it

[storage]
comment = General Storage
path = /home/stizzle/Storage
guest ok = yes
browsable = yes
writable = yes
security = share
public = yes

Hi **Whiteice**

What happens if you try:
```
smbclient -L //xxx.xxx.xxx.xxx -Uguest
```
Enter that in a BASH shell on the Samba **Server** (not client machine!) Don't use the loopback address (127.0.0.0) - use the LAN IP address. I guess just press return for the Guest password (if you have specifically allowed blank passwords in smb.conf)...

The response in the terminal should be either an error message or a list of the shares on your Samba server... :D If it's an error message can you post it here - please!

Should you get the happy response of a list of shares, from your Samba Server, then can you put in:
```
smbclient //xxx.xxx.xxx.xxx/storage -Uguest
```
To see if you can manually connect to your **storage** disk share. Again plug the output here if it is/contains an error message.

All the best
Bob

P.S. I am presuming you are familar with basic networking stuff. To get your Servers IP address run **ifconfig**. Copy the address from the **inet addr:** [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR]  field on your active ethernet/wireless-LAN adapter in the list (assuming you are still using IPv4 - are you??!! TIME TO CHANGE... NOW!! :popcorn: )

---

### Post by Morbius1 on 2011-05-13
I'm not really sure what your question is. If the question is that you have a guest share and you want to require usernames and passwords then change your share definition to this:
```
[storage]
comment = General Storage
path = /home/stizzle/Storage
guest ok = no
browsable = yes
writable = yes

```You will need to create local users on the server and then give them samba passwords.

If the problem is accessibility as a guest share then there are other things to consider:

[1] We really need the whole smb.conf to do a debug so you might want to post the output of the following command:
```
testparm -s
```[2] In order for a remote guest ( or any remote user other than you ) to have write access to that share the Linux file permissions must be in sync with samba authorizations. So if you do a:
```
ls -dl /home/stizzle/Storage
```it has to come back with: drwxrwxrwx

If it doesn't then make it so:
```
sudo chmod 777 /home/stizzle/Storage
```If you chmod and it has no affect then "Storage" is a mountpoint for an NTFS or FAT32 partition and there are a few minor things that need to be done.

---

### Post by Whiteice on 2011-05-14
bobwyajnr I tried the command and I get a prompt asking for a guest password and i honestly do not know where to look for the password for it. I have tried my common passwords and they do not work. Do i have to create a specific user names guest and assign a password? 

Morbius1 I am trying to have a windows user connect to the server and instead of being prompted for a user login I would like it to just connect without the prompt or login.

---

### Post by Morbius1 on 2011-05-14
> Morbius1 I am trying to have a windows user connect to the server and  instead of being prompted for a user login I would like it to just  connect without the prompt or login.Since you didn't follow my earlier suggestion I'll give you another:
Add one more line to your share definition:
> [storage]
comment = General Storage
path = /home/stizzle/Storage
guest ok = yes
browsable = yes
writable = yes
security = share
**[COLOR=Blue]force user = stizzle[/COLOR]**
public = yes     
Then restart samba:
```
sudo service smbd restart
```I'm assuming that "stizzle" is a username. This does not appear to be a Samba problem it looks like a Linux permissions problem. If "stizzle" can access Storage so will the remote guest with the addition of the "force user" line.

---

### Post by bobwyajnr on 2011-05-14
> **Whiteice said:**
> 
**Morbius1** I am trying to have a windows user connect to the server and instead of being prompted for a user login I would like it to just connect without the prompt or login.

Please can you follow Morbius1's recommendations or say that you don't understand them (you've chosen the 3rd way)!! :popcorn:

[LIST=1]
[*] Type in a terminal:
```
testparm -s
```
This will check that your Samba Server configuration file is correct and will spit out any errors. You don't need to post the whole output here - just any errors (most of the output will just be a dump of the **/etc/samba/smb.conf** file)



[*] Type in a terminal:
```
ls -dl /home/stizzle/Storage
```This will let us know what (UNIX user) permissions your 'Drop Folder' has. If you log in, via Samba, you don't suddenly get root access your filesystem! That would be bad - real bad!!:popcorn:
[/LIST]

Part of the point of asking for help is to... listen for the answers!! :popcorn:

Don't worry about my suggestions. **Morbius1** has made suggestions that will target your problem a bit more quickly.

[COLOR="Red"]NB If you are going to mess about with your Samba configuration file then enter the following first!![/COLOR]
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
[COLOR="Red"]At least then you have a backup of your current configuration!!
[/COLOR]

If you want equivalent of 'everyone access' (on Windows) to share you'll probably need to add:
```
null passwords = yes
```
to the **[Global]** section of your **smb.conf** file:
```
gksu gedit /etc/samba/smb.conf
```
if it is not already present in the file...

Bob

---

### Post by Morbius1 on 2011-05-14
"null passwords = yes" is just that. It allows client access to accounts that have null passwords. The "account" refers to the linux account and it's samba password. The Linux server would have to create an account and give it a null samba password for that option to have any affect:
```
sudo smbpasswd -an user-name
```In this case whatever password the Windows client is passing is being ignored by Samba since it's a guest share.

---

