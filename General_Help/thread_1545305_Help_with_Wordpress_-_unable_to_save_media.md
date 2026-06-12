---
title: "Help with Wordpress - unable to save media"
date: 2010-08-03
forum: General Help
---

### Post by Nitch on 2010-08-03
Hello,

Quick bit of background...joined the forum ages ago when someone suggested I try Ubuntu.  I tried it but was having issues with the wifi and as I was going away and needed wifi, I went back to XP so didn't get a lot of experience.  Anyway, thought I'd give it another go the other day and here I am...

I've been trying to develop a simple wordpress site using my Ubuntu machine but I'm still a novice and very used to Windows and it's lack of security!

Anyway I've installed XAMPP and Wordpress and got it running ok but when I try to add plugins or upload images or videos, it fails saying they can't be saved. I guess this is down to permissions but I can't see how to set it so these files can be saved?

Any help with this would be great.  Many thanks

---

### Post by Nitch on 2010-08-04
Anyone know how to set the permissions on the folder where the media is saved? Or could it be the database causing the problem? 

Thanks

---

### Post by chopinhauer on 2010-08-04
> **Nitch said:**
> Anyone know how to set the permissions on the folder where the media is saved? Or could it be the database causing the problem? 


Your wp-content/plugins wp-content/themes and wp-content/uploads should have read and write permissions for the user that runs Apache (www-data). You can do it like this:
```

cd /path/to/your/wordpress/installation
chmod a+rw wp-content/{plugins,themes,uploads}

```

---

### Post by Nitch on 2010-08-04
Brilliant, thanks for that.  I'll have a look when I get home tonight.

Thanks again

---

### Post by chopinhauer on 2010-08-04
I should probably add that if you used the Ubuntu package to install Wordpress (using the latest tarball from [WordPress.org](http://wordpress.org) is a better idea if you ask me, even if more complicated), the path to your install will be /usr/share/wordpress.

---

### Post by trentscott on 2010-08-04
> **chopinhauer said:**
> Your wp-content/plugins wp-content/themes and wp-content/uploads should have read and write permissions for the user that runs Apache (www-data). You can do it like this:
```

cd /path/to/your/wordpress/installation
chmod a+rw wp-content/{plugins,themes,uploads}

```

This should work! I had to do the same thing.

---

### Post by Script Warlock on 2010-09-22
thanks for this brilliant solution ... it works for me..

---

