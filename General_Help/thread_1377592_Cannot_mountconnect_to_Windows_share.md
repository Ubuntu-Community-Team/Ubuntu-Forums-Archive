---
title: "Cannot mount/connect to Windows share"
date: 2010-01-10
forum: General Help
---

### Post by Ugluk on 2010-01-10
I cannot connect to a share on Windows XP machine, because it rejects my password. I'm using correct username and password.
When running from console, smbclient's error message is: session setup failed: NT_STATUS_LOGON_FAILURE
I can connect to said share from other Windows machine.

What can be a problem?

---

### Post by mk1w86 on 2010-01-10
When Ubuntu asks for a password try entering guest as the username and leave the password blank.

You might also have to check sharing settings on XP and the folder permissions you are trying to share.

---

### Post by Ugluk on 2010-01-10
I've checked share permissions and added guest, but it still do not work.

Anonymous login successful
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

---

### Post by Morbius1 on 2010-01-10
I know this isn't going to make any sense but could you post the smb.conf from the ubuntu machine:

**testparm -s**

It could be that you're not encrypting the password and it would fail even if enabled guest on the Win2K server.

---

### Post by Ugluk on 2010-01-10
I don't have samba, only smbclient and related stuff.

smb.conf:

[http://pastebin.ubuntu.com/354663/](http://pastebin.ubuntu.com/354663/)

---

### Post by Ugluk on 2010-01-11
bump!

---

### Post by cariboo on 2010-01-13
You don't need Samba to connect to a Windows share. The username and password should be that of the Windows computer you are trying to connect to, not your username and password on your Ubuntu system. You will have to add your Windows username and poassword by using the following commands.

```
sudo smbpasswd -L -a <username>
```

and 

```
sudo smbpasswd -L -e <username>
```

---

### Post by Ugluk on 2010-01-13
It doesn't seems to work:
```
~$ sudo smbpasswd -L -a xxx <-- my Windows account name
New SMB password: <-- my Windows password
Retype new SMB password:
Failed to add entry for user xxx.
~$ sudo smbpasswd -L -e xxx
Failed to find user xxx in passdb backend.
~$
```
Did I get something wrong?

---

### Post by Morbius1 on 2010-01-14
You can only create a samba password for users who have an existing account on that machine. 

So first you need to create a user on the Ubuntu client:

```
sudo useradd username
```Better yet create a local user without a shell account:

```
sudo useradd -s /bin/true username
```Then create a samba password for that user:

```
sudo smbpasswd -L -a <username>
sudo smbpasswd -L -e <username>
```BTW, I've learned a long time ago never to make absolute statements about anything pertaining to samba but I don't quite understand why you're creating a samba user for the Windows server on the Linux client. If you were trying to access a share on the Linux machine from windows and you required authentication then you'd need a samba username and password on the Linux box for the Windows client.

The other thing is that you said you changed the share on the Windows server to allow guest access so you shouldn't need a username and password anywhere.

But, I'm always open to learning something new.

---

### Post by Ugluk on 2010-01-14
Why do you suggest this nonsense? I stated clearly what my problem is.

---

### Post by Morbius1 on 2010-01-14
> **Ugluk said:**
> Why do you suggest this nonsense? I stated clearly what my problem is.

Was that directed at me?

My post ( #9)  was in response to your post (# Eight ) . You're trying to create a samba password for the windows server user on the linux client and you got this error:
```
Failed to find user xxx in passdb backend.

```You got that error because you can only create a samba password for users with an account on the linux client. I gave you steps to create that user.

The rest of my post was about why you were creating  users on the client in the first place. For my money it's either a Windows permissions problem, a Widows firewall or anti-virus problem, or smbclient cant find your windows machine by netbios name.

Did you try to access the windows box by ip address.

---

### Post by Ugluk on 2010-01-15
Antiviruses do not scan SMB traffic. It cannot be a permissions or firewall problem, because I can connect from other (Windows Vista) machine in the same network, with same credentials successfully. Yes, I'm using IP address to connect in both cases.

---

### Post by Morbius1 on 2010-01-15
> **Ugluk said:**
> Antiviruses do not scan SMB traffic. 
That would make for a very ineffective antivirus wouldn't it. Have you tried to disable your firewall and antivirus software to see if it has any affect. Or are you absolutely sure you know what the cause of the problem is not.

---

### Post by Ugluk on 2010-01-15
*Obviously*, firewall accept SMB connections from my network, so it definitely not blocking out a single machine in it. I don't have resident antivirus scanner.

---

### Post by Ugluk on 2010-01-16
bump

---

### Post by jamesisin on 2010-01-16
There are two locations for permissions on the XP machine.  You will want to make certain that they are both set correctly.  Share permissions are under the Share tab (as I recall there is a button which brings up the permissions dialog) and the file/browse permissions are under the Permissions tab.

Also, you will want to make certain that you are using the correct domain name when you send your credentials.  Is your XP machine attached to a domain?  If not, is it WORKGROUP?

---

### Post by Ugluk on 2010-01-16
Yes, they are set correctly because I can access it with the same credentials from my Vista machine. Yes, I'm using both WORKGROUP and MSHOME as domain name, but to no avail.
No, my XP machine is not in domain.

---

### Post by jamesisin on 2010-01-16
Do you have to manually enter your credentials when you access the share from another of your Windows machines (or are you taken directly into the share with no credentials dialog)?

---

### Post by Ugluk on 2010-01-16
Yes, I'm presented with credential dialog box.

---

### Post by jamesisin on 2010-01-16
So the share is set to require credentials (that is, you have not enabled Guest Access)?

---

### Post by Ugluk on 2010-01-16
Share has a Guest having full access to it. Also, Guest account is enabled.

P.S. Why should I use guest account to connect to it? It's insecure.

---

### Post by jamesisin on 2010-01-16
I am not suggesting that you should allow guest access.  It has its purpose (especially in read-only situations), but it is less secure.

However, if you have guest access enabled...

why do your Windows machines prompt you for credentials?

If that's the case, then it sounds like your (file) permissions are not set correctly.

---

### Post by Ugluk on 2010-01-16
File access is set to Everybody:Full control.

When I'm trying to connect to it especially as guest, I'm keeping asked for it's password.

---

### Post by jamesisin on 2010-01-16
Well, that's about as wide open as it gets.

Could you attach a screen shot of your Share permissions and the Security tab from Properties on the folder you are sharing for me?

---

### Post by Ugluk on 2010-01-16
*rolls eyes* sure...

---

### Post by jamesisin on 2010-01-17
So you have:

Permissions tab; 1. System 2. local admin 3. Bce (Everyone?) 4. local user account

Share tab; 1. Everyone 2. local user account

I am a little concerned that there does not seem to be Creator/Owner in your Permissions tab, but that may be ok.  (Unless Bce turns out to be Creator/Owner in which case remove it from the Share tab.)

If you are turning guest access off, you will want to remove Everyone from the Share tab.

Is Everyone inherited in the Permissions tab or did you add it there.  If you added it remove it.

Open Nautilus and enter smb://sandy/testshare into the Location field.  It should prompt for a credentials.  Use your XP username (like Toctb) and that associated password.  Be mindful you are using the correct domain (workgroup or mshome, whichever is correct for that XP machine).

If it fails, try attaching to smb://sandy to see if you can get the machine's share list.

Tell me how this goes.

---

### Post by Ugluk on 2010-01-17
Nautilis just keeps asking for a password, and don't accept it for either guest or account name, whether connecting or viewing share list. I even had created a special account with ascii-only characters in name and password, but it still won't accept it.

---

### Post by Ugluk on 2010-01-18
bump

---

### Post by jamesisin on 2010-01-18
Did you follow all of my directions, because I don't see you making much mention of them?

---

### Post by louieb on 2010-01-18
For what its worth try CIFS. Once setup has the advantage of being very easy to use.
[Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba")

---

### Post by Ugluk on 2010-01-19
```
client ntlmv2 auth = yes
```
This fixed the problem.

But why the hell the manual says it's for Vista shares when I need it to connect to XP one?

And why the hell it's not on by default? NTLM2 already was in Windows 2000...

---

