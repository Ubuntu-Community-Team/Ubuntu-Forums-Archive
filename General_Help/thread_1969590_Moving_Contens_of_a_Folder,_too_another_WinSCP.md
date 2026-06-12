---
title: "Moving Contens of a Folder, too another: WinSCP"
date: 2012-04-30
forum: General Help
---

### Post by mrchasez on 2012-04-30
I have Sudo permissions, however.
I am using WinSCP. 

I need too move the contents of /var/www/multicraft
Too /var/www/

(Just the contents, Not the multicraft folder)

So i can go to MYIP and have the website.

Not MYIP/Multicraft

When i try and just Select all, and drag them into the new folder using WinSCP i get this error

Command 'mv -f "assets" "/var/www/assets"'
failed with return code 1 and error message
mv: cannot move `assets' to `/var/www/assets': Permission denied.

Which makes sense, since its not using Sudo command.

So how do i move the contents too the new directory?

---

### Post by wyliecoyoteuk on 2012-04-30
You have to login as root.

[http://winscp.net/eng/docs/faq_su](http://winscp.net/eng/docs/faq_su)

What might be easier is to use PuTTY.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

then ```
sudo mv /var/www/multicraft/*.* /var/www/*.*
```

oops, no recursion option in mv.

might be better to do 
```
sudo cp -R /var/www/multicraft/*.* /var/www/*.* 
```

then
```
sudo rm -R /var/www/multicraft
```

---

### Post by mrchasez on 2012-04-30
> **wyliecoyoteuk said:**
> You have to login as root.

[http://winscp.net/eng/docs/faq_su](http://winscp.net/eng/docs/faq_su)

What might be easier is to use PuTTY.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

then ```
sudo mv /var/www/multicraft/*.* /var/www/*.*
```

oops, no recursion option in mv.

might be better to do 
```
sudo cp -R /var/www/multicraft/*.* /var/www/*.* 
```

then
```
sudo rm -R /var/www/multicraft
```

I have Putty.

****, The first one didnt work and i deleted my DAMN FILES
SHIIIT

---

