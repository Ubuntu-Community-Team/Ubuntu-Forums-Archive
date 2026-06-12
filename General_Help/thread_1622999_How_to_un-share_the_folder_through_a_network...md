---
title: "How to un-share the folder through a network..?"
date: 2010-11-16
forum: General Help
---

### Post by tajiknomi on 2010-11-16
[SIZE=2]

I had share my folder through network with other PC,now i want to Rivert(un-share) this,how can i..?

I had right-click on that folder but i didn't get any option for that....it's my first time of sharing data via **samba**...

that's All...
[/SIZE]

---

### Post by pricetech on 2010-11-16
Check your other post with the same question for my response.

---

### Post by Morbius1 on 2010-11-16
> [SIZE=2]I had right-click on that folder but i didn't get any option for that.[/SIZE]It looks like you're using Nautilus-share so just go back and uncheck all the boxes. If you shared a folder that no longer exists then you can remove the share definition from the terminal:
```
net usershare delete [COLOR=Blue]*sharename*[/COLOR]
```Or you can go into:
```
/var/lib/samba/usershares
```and just delete the share definition file.

---

### Post by tajiknomi on 2010-11-17
[@pricetech]("http://ubuntuforums.org/member.php?u=567037")

[SIZE=2]Actually i had posted it in general Forums and for about 30min,i wait,but no one replies,so i thought that i had post it in Wrong Forums therefore...

@[/SIZE][Morbius1]("http://ubuntuforums.org/member.php?u=982144")
                [SIZE=2] I did it by "**net usershare Delete share-name **"

but can u explain a little bit that whats is the difference b/w **Samba**[/SIZE][SIZE=2] and **nautilus-share**..?[/SIZE]
[SIZE=2]And what will be the **benefit** of using Samba..?[/SIZE]

---

### Post by Morbius1 on 2010-11-17
> [SIZE=2] but can u explain a little bit that whats is the difference b/w **Samba**[/SIZE][SIZE=2] and **nautilus-share**..?[/SIZE]It's probably the way I worded my post but Nautilus-share is Samba. It's been part of Samba for years. There are two completely different methods of creating a Samba share:

**Classic-shares:** This is the original way of creating shares and it creates share definitions in /etc/samba/smb.conf. You must be root to create shares.

**Usershares:** This method creates shares in /var/lib/samba/usershares. Nautilus-shares is actually a package that implements usershares through Nautilus. It's purpose is to allow an ordinary user to create any folder he owns and hence you do not need to become root to share.

As far as one method having an advantage over another, it depends on your requirements. Nautilus-shares are far easier to implement, you do not have to become root, and it automatically adjusts permissions on the shared folder so that samba authentication and linux file permissions are in sync.

Classic-shares are slightly more difficult to set up, you must be root, and linux file permissions have to be set up independently. But Classic-shares offers a level control over individual shares that is not achievable in usershares. You could for example set up a share that is accessible by only one remote user only if that remote user is on a system with a specific ip address. 

Each method has it's place and both methods can be used together but I would not recommend that. It becomes a management issue of what method is being used with which folder and you get into trouble when you use both methods on the same folder. I think that for the average user in a normal peer-to-peer like network Nautilus-share is all that's needed.

---

