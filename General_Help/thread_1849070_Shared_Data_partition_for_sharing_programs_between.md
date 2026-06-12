---
title: "Shared Data partition for sharing programs between Fedora and Ubuntu."
date: 2011-09-23
forum: General Help
---

### Post by YQ002lc2 on 2011-09-23
I presently use Fedora and Ubuntu.

I want to share user profiles and data in programs such as:

~/.mozilla ~/.thunderbird ~/.purple ~/.VirtualBox .... and so forth.


Does anyone have any experience and know-how setting something like this up? 

I guess I need to:

1. Set up some partition  using a file system which both OSes can read.
2. Move the Program's user data there.
3. Create some type of symbolic links to the Shared data partition files in the locations they would otherwise be in the respective home directories.

Does that sound right?

Any comments, recommendations, and instructions are much appreciated.

Thanks,

jpinson

---

### Post by Dangertux on 2011-09-23
In my opinion you should just create an ext3 partition where the data is stored, and mount it in each distro, they should be able to read it. As far as profiles go just point the appropriate apps at the shared partition.

Using links would be fine as well, just one thing though, if you encrypt the home directory it will break the link.

---

### Post by YQ002lc2 on 2011-09-23
Thank you Dangertux,

I guess my only question now is how to "point the appropriate apps to the shared partition"?

thanks,

jp

---

### Post by coffeecat on 2011-09-23
One important thing to check is your UID (user identity) in Fedora and Ubuntu. In Ubuntu, if your account is the first created account, it will be 1000. In Fedora, account UIDs start at 500. Or at least they did until recently. I seem to remember that Fedora was planning to change things so that UIDs started at 1000. Whether they have done already, or will do so in the future, or whether I have misremembered, I don't know, but check this. If you try to share profiles with accounts with different UIDs you will run into permissions problems.

If your Fedora account is 500, I guess the easiest thing to do would be to create a new account in Fedora and specify a UID of 1000.

---

### Post by garvinrick4 on 2011-09-23
+1 with coffeecat
Tried to share a /home and permission problems with different UID's was not a good thing
at all. Edited and took out rambling on coffeecat said my experience with same.

---

### Post by Dangertux on 2011-09-23
Starting in Fedora 16 the default UID is 1000.

However, you don't have to create a new user, you can simply :

```

sudo umod -u 1000 username

```

As far as the profiles in question it just depends on the application, you may wish to consult the documentation for that or like stated already just create links.

---

### Post by YQ002lc2 on 2011-09-24
Thank you all for your comments and suggestions.

I've finally reached a solution and editing my post to reflect it here.

I backed up my ubuntu home.

> sudo cp /directory /backup_directory/

I changed the permissions back to 777 to make things a bit easier to work with.

> sudo chmod 777 /directory/of/backup/ -R


I reinstalled ubuntu with the following partitions:

Swap
Shared Data (ext4)
Ubuntu(ext4)
Empty

I installed Fedora on the empty partition. (with the boot information being stored on the first sector of the Fedora partition.)

I rebooted into Ubuntu and updated grub to detect fedora
> sudo update-grub



As far as the topic at hand is concerned:

1. I moved my .whateverprogram files to the shared directory.
2. I deleted any existing .whateverprogram files in my existing installation's home directory.
3. I used the following command in both Ubuntu and Fedora to create symbolic links.

> ln -s /directory/for/referenced/files/.WhateverProgram /newly/created/symbolic/link/.WhateverProgram

4. As noted by Dangertux, Fedora 16 's default UID is 1000, so I didn't have to make any changes there.

5. I manually mounted the shared partition.
6. I then launched the various programs which referenced the shared directory without a hitch.

hurray! 


Comment:
It seems the "umod" command does not exist under fedora or at least I couldn't find it. I ran sudo yum install umod....
So the following command didn't work for me. > sudo umod -u 1000 username
However, it seems fedora has graphical tool under Administration-->Users and groups  to manage all of that.


Questions remaining:
1. how should I configure my systems to automatically mount the shared drive on startup?
2. If I later want to encrypt my home directories, is there another equally simple solution to reference the shared configuration files on the shared partition?


Thanks and all the best,

jp

---

