---
title: "Make Ubiquity installer work with SLiM"
date: 2010-11-15
forum: General Help
---

### Post by beastrace91 on 2010-11-15
Howdy All,

So I am trying to make the Ubiquity installer work with the SLiM login manager. I want when you check "auto login" for it to actually configure auto login in slim. I opened the **user-setup-apply** file in */usr/lib/ubiquity/user-setuo* and I added this chunk for code:

```
if $chroot $ROOT [ -f /etc/slim.conf]; then
				#configure slim autologin
				$log $chroot $ROOT sed -i$BACKUP -r \
-e "s/^#?default_user.*\$/default_user $USER/" \
					/etc/slim.conf
			fi
```

I also tried"

```
if $chroot $ROOT [ -f /etc/slim.conf]; then
				#configure slim autologin
				mv $ROOT/etc/slim.conf $ROOT/etc/slim.conf.old
				sed 's/default_user        bodhi/default_user  $USER/g' $ROOT/etc/slim.conf.old > $ROOT/etc/slim.conf
fi
```

In both instances I then recreated my live disc with the new user-setup-apply file and tried to install, both chunks of code failed to work. Any ideas what I am doing wrong here?

~Jeff

---

