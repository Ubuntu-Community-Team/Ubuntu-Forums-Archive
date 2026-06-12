---
title: "Accessing share rights to NFTS file on USB drive"
date: 2009-09-12
forum: General Help
---

### Post by ponto1963 on 2009-09-12
Help

My wife's XP pc has crashed, most of her files are a WD USB hard drive that was able to be accessed over our home net via her computer. We have 5 children, so have a couple of laptops plus my Ubuntu machine, all of which used to access files from her machine.

I've attached her external drive to my machine but can't seem to be able to make it share able in!!

the following error shows
--------------------------------------

'net usershare' returned error 255: net usershare add: cannot share path /media/My Book/Music as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this

---------------------------------------
I'm not quite sure what I need to do to access permissions.

Please help, I'm still in the learning curve with Ubuntu.:confused:

---

### Post by kidders on 2009-09-13
Hi there,

The error you mentioned is presumably a security measure designed to prevent unprivileged users of your box sharing system files (accidentally or otherwise). The problem stems from the fact that NTFS filesystems do not support the traditional *nix security model, so your computer has no reliable way to determine who should have access to them.

There *are* other ways around this problem, but the solution suggested in your error message is to remove the sharing restriction, by modifying your Linux box's Windows file sharing configuration. If you're happy to do that, try the following:

```
# Become root
sudo su

# Open smb.conf
nano -w /etc/samba/smb.conf
```

The file is divided into sections, labelled with words inside square brackets (eg [global] or [homes]). Find the [global] section, and look through it for any configuration options that seem to state the opposite of what you want to do (ie "usershare owner only = true") ... if you find any, just remove them. Then, immediately underneath "[global]", add **usershare owner only = false** as suggested. Hit CTRL + X to quit the text editor.

```
# Restart Windows file sharing
/etc/init.d/samba restart

# Give up root privileges
exit
```

You *should* find that you can now share your NTFS filesystem. That said, the next issue you'll very likely run into is remote access to the files it contains. For lack of a clearer idea of what to do, your Linux box may prevent your users modifying the shared files. This is an issue that also crops up with FAT filesystems, and is covered again and again on these forums, so you shouldn't have too much trouble with it. The simplest (but least secure) solution is to explicitly grant full read/write access to the filesystem. Once that's working, you can curtail individual users' access with Samba, if you want to.

I hope that helps.

---

### Post by ponto1963 on 2009-09-13
Many thanks, seems to work. It's a home network so don't need any restrictions on access, :-)

:popcorn:

---

