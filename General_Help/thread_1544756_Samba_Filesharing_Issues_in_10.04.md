---
title: "Samba Filesharing Issues in 10.04"
date: 2010-08-02
forum: General Help
---

### Post by RustyOrbit on 2010-08-02
My Situation has two small problems that together amount to a  frustrating situation.
I have a Desktop and a netbook dual booting  Ubuntu 10.04 and win7 I have installed a samba server & GUI on both  computers' linux halves (by instaling the Samba package) (smbclient is  also installed on both)
     when trying to share between both  ubuntus about half the time when I open the network from the places menu  everything will work perfectly, the other half i have a medly of  errors. sometimes I will get the "failed to retrieve share list from  server" error, and sometimes i will just not see any entries in the  "windows network" sub-menu. and even when it works sometimes i see  entries for the other computers on the network before entering into the  windows network sub-menu and sometimes those entries contain access to  the shares on those computers, sometimes I have to go through the  windows network path.

usually these problems are solved by making  sure that the computer hosting the share is awake and rebooting the  computer that is trying to access a share. this leads me to believe that  the problem stems from the fact that the netbook falls asleep or  hibernates, interfering with samba's serving ability, and that even once  the server comes back the client doesn't recognize it unless the server  is functioning when the client boots.

An interesting occurrence  is that if i Ping the host from the client when no entries appear in the  network, entries appear and it works. even stranger is that pinging the  host also makes the other computers on the network appear, including  the client itself.

it is an easy enough workaround, but very  strange behavior. 


the second issue is that i cant mount  these shares to a directory in my filesystem, even when i can see and  access them through the GUI. the command

#sudo mount -t cifs  smb://nibbler/filesystem/ /home/dean/smbtest

returns

#Mounting  cifs URL not implemented yet. Attempt to mount smb://nibbler/filesystem
#No  ip address specified and hostname not found

nibbler is the host  and filesystem is the share
replacing host name nibbler with the ip  address of nibbler returns a similar error. 

the reason I am  trying to mount the share in this way is because i want to use the #cp  -u command to manually sync the music folders on each machine, and I  cant point cp at a network location

---

