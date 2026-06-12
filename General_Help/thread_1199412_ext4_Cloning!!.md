---
title: "ext4 Cloning!?!"
date: 2009-06-28
forum: General Help
---

### Post by xenogia on 2009-06-28
I am wanting to back up my OS partition that is currently using the ext4 file system and wondering what software (free of course) that people would recommend me to do the job?

---

### Post by moster on 2009-06-28
Restart to WINDOWS and then ... I am joking :)

Go to [http://clonezilla.org/]("http://clonezilla.org/") People said it is best tool for that..

---

### Post by xenogia on 2009-06-28
I'll check it out :)

---

### Post by VastOne on 2009-06-28
> **xenogia said:**
> I am wanting to back up my OS partition that is currently using the ext4 file system and wondering what software (free of course) that people would recommend me to do the job?

What are you wanting to clone to? Another drive?  

If so, dd works very well but read all you can about it first 

I build computers for clients and put a stock image on all of them and use dd for it's speed and simplicity.

dd is already on your system

---

### Post by ericab on 2009-06-28
last i heard clonezilla doesnt support ext4 yet...
someone correct me ?

---

### Post by xenogia on 2009-06-28
> **VastOne said:**
> What are you wanting to clone to? Another drive?  

If so, dd works very well but read all you can about it first 

I build computers for clients and put a stock image on all of them and use dd for it's speed and simplicity.

dd is already on your system


I am wanting to back up to another ext4 partition, and what exactly is dd?

---

### Post by VastOne on 2009-06-28
> **xenogia said:**
> I am wanting to back up to another ext4 partition, and what exactly is dd?

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by xenogia on 2009-06-28
> **VastOne said:**
> [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Thanks for the advice.

---

### Post by moster on 2009-06-30
> **ericab said:**
> last i heard clonezilla doesnt support ext4 yet...
someone correct me ?

I seriously doubt they would lie on their site on something like that. But you never know till you try :D

---

### Post by mcduck on 2009-06-30
> **ericab said:**
> last i heard clonezilla doesnt support ext4 yet...
someone correct me ?

It can clone any filesystem.

For supported filesystems only actually used blocks are copied, for unsupported filesystems it simply copies the whole partition, including unused blocks (like dd does, and actually in these situations Clonezilla uses dd to do the job).

..and yes, they do list Ext4 as supported filesystem. :)

---

### Post by xenogia on 2009-06-30
> **mcduck said:**
> It can clone any filesystem.

For supported filesystems only actually used blocks are copied, for unsupported filesystems it simply copies the whole partition, including unused blocks (like dd does, and actually in these situations Clonezilla uses dd to do the job).

..and yes, they do list Ext4 as supported filesystem. :)

I personally tested it with the ext4 filesystem and Clonezilla works absolutely beautifully :)

---

