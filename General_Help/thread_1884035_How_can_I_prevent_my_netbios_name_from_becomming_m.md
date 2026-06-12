---
title: "How can I prevent my netbios name from becomming my hostname in Samba"
date: 2011-11-20
forum: General Help
---

### Post by Morbius1 on 2011-11-20
_**Scope**_:
I have a test machine that when connected to my local network has shares that can be browsed to and accessed by it's hostname. It does it by hostname by automatically assigning my hostname to the "netbios name" in samba. I'm trying to find out what conditions have to be present to prevent that default behavior from happening.

_**My Setup:**_
Currently running Xubuntu 11.04 on that box.

Relevant content of my /etc/hosts file:
> 127.0.0.1    localhost
127.0.1.1    morbiusxContent of hostname:
```
cat /etc/hostname
morbiusx
```I have not added a "netbios name" parameter to my /etc/samba/smb.conf file:
```
testparm | grep "netbios name" 
```Comes up blank:
> Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[homes]"
Processing section "[homes-admin]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions 
[COLOR=Blue]< I hit enter since I didn't apply the "-s" switch to my testparm command which would suppresses this request for an enter response[/COLOR] >

morbius1@morbiusx ~ $ Unfortunately that doesn't prove that I didn't add "netbios name" to my smb.conf since had I added it but made it match the default value testparm would also not list it. So as further proof I ran the following command:
```
cat /etc/samba/smb.conf | grep "netbios name"
```That returns this which as you can see is only a comment:
> # on a per machine basis. The %m gets replaced with the netbios name_**Some Background:**_
My first step in this expedition was to run the following command:
> testparm -v | grep "netbios name"That does indeed list my hostname:
> Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[homes]"
Processing section "[homes-admin]"
Processing section "[ISO]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
< enter >

    netbios name = MORBIUSX
[COLOR=Blue][I]For those of you who are not familiar with the "-v" switch I offer the following explanation:

Smb.conf is a list of overrides and additions so it does not reflect the complete configuration of samba only the changes. Running testparm by itself only reports on the contents of smb.conf and lists only those parameters that are set to values that are different from the defaults. The "-v" switch will list all of the default parameters and reflect either their default values or values that were modified by smb.conf as well as any additions in smb.conf. 
[/I][/COLOR]
So if "-v" shows my netbios name as matching my hostname and I did not explicitly add that parameter to my smb.conf I concluded that it must be in the defaults. How do I determine the pure default settings? The only way I know of is to force testparm to use the "-v" switch against a dummy empty file so that the only thing I would get back are the defaults:
```
testparm -v /dev/null | grep "netbios name"
```> Load smb config files from /dev/null
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
< enter >

    netbios name = MORBIUSX
So it's in the defaults itself but I don't know how to stop this from happening. 

_**What I've tried so far:**_
First I disconnected the machine from my router ( an antique DLink DI-604 ) just in case it's adding anything to this process and rebooted the machine. I even disabled avahi from starting at boot and rebooted again but in both cases my netbios name ends up to be my hostname. As a final experiment I changed the name to morbiusy in both /etc/hosts and /etc/hostname, did a reboot, and checked testparm -v /dev/null. It is now set to "morbiusy". Reconnected my machine to the router and now have to access my shares by "morbiusy". 

It appears that Samba reads the hosts file ( or possibly the hostname file directly ), sets the netbios name, and makes it part of it's default settings. It would seem to me that the only way to prevent this  behavior would be to remove the hostname reference from /etc/hosts and/or /etc/hostname and I don't see how that could happen by itself.

Can anyone think of any other way to break this default behavior?

---

### Post by redmk2 on 2011-11-20
> **Morbius1 said:**
> _**Scope**_:
I have a test machine that when connected to my local network has shares that can be browsed to and accessed by it's hostname. It does it by hostname by automatically assigning my hostname to the "netbios name" in samba. I'm trying to find out what conditions have to be present to prevent that default behavior from happening.

<snip>

Can anyone think of any other way to break this default behavior?

Why do you ask?  Samba can interact with the kernel.  It may not directly read any file at all.

You can always *break this **default** behavior * by defining the netbios name in the smb.conf file with a name less than 15 characters```
netbios name = <myNetBiosName>
```

But you already knew that.  :-)

---

### Post by Morbius1 on 2011-11-20
Thanks for your response.

It does sound like an odd request doesn't it. 

There have been  a few posts lately that have stated that the only way to have the netbios name in samba match the hostname is for the user to explicitly add "netbios name = <hostname>" to smb.conf.

I believe that the netbios to hostname match happens by default in a typical home lan as I have illustrated above. In fact I can't figure out how to stop it from happening. 

I'm just trying to figure out if there is some set of circumstances that would have to be present to prevent this from happening.

---

### Post by Paddy Landau on 2011-11-28
> **Morbius1 said:**
> [QUOTE=Paddy Landau;11493217]Out of interest, I changed [FONT=Fixedsys]/etc/hostname[/FONT] to have a name different from [FONT=Fixedsys]/etc/hosts[/FONT], removed [FONT=Fixedsys]netbios name[/FONT] from [FONT=Fixedsys]smb.conf[/FONT], rebooted and ran [FONT=Fixedsys]testparm -v[/FONT]. It seems that Samba explicitly uses [FONT=Fixedsys]/etc/hostname[/FONT] and not [FONT=Fixedsys]/etc/hosts[/FONT].
 
 (I don't know what problems having two different names would cause, so I have set the names back to being equal again.)
If you check /etc/hosts after changing just /etc/hostname and then reboot does 127.0.1.1 show the new hostname or the old one?[/QUOTE]
I'm not sure of what you are asking. This is what I did:


[LIST]
[*][FONT=Fixedsys]/etc/hostname[/FONT] contained:```
CompName
```
[*][FONT=Fixedsys]/etc/hosts[/FONT] contained (showing the relevant line only):```
127.0.1.1 Comp127
```
[*]Removed [FONT=Fixedsys]netbios name[/FONT] from [FONT=Fixedsys]/etc/samba/smb.conf[/FONT].
[/LIST]

After rebooting, the computer name was [FONT=Fixedsys]CompName[/FONT], [FONT=Fixedsys]testparm -v[/FONT] showed [FONT=Fixedsys]netbios name = [/FONT][FONT=Fixedsys]COMPNAME[/FONT], and accessing the shares over the LAN found the name [FONT=Fixedsys]COMPNAME[/FONT]. I do not know for what [FONT=Fixedsys]Comp127[/FONT] would have been used.

If I add to [FONT=Fixedsys]smb.conf[/FONT] yet a different [FONT=Fixedsys]netbios name[/FONT], e.g. [FONT=Fixedsys]CompNet[/FONT], then testparm -v shows [FONT=Fixedsys]COMPNET[/FONT], and I can access the public shares from the LAN via [FONT=Fixedsys]COMPNET[/FONT].

If you are asking whether or not the file [FONT=Fixedsys]/etc/hosts[/FONT] was changed automatically, the answer is no, it wasn't. I had to manually set the files back to their correct settings.

---

### Post by Morbius1 on 2011-11-28
> If you are asking whether or not the file [FONT=Fixedsys]/etc/hosts[/FONT] was changed automatically, the answer is noYes, that was the question I was asking. When I wanted to change the hostname I always change both /etc/hostname and /etc/hosts together because bad things happen to sudo if you don't.

But it is interesting that just changing the name in /etc/hostname will change the default "netbios name" in samba to the new name and that new name is now the one that is visible on the lan.

It appears that it's getting harder and harder for me to break the default behavior of Samba in this regard :wink:.

I very much appreciate your input.

---

### Post by Paddy Landau on 2011-11-28
> **Morbius1 said:**
> It appears that it's getting harder and harder for me to break the default behavior of Samba in this regard :wink:.
If, as I understand it (and I may be wrong), this is the specified behaviour of Samba, then you cannot break it without first breaking Samba.

---

