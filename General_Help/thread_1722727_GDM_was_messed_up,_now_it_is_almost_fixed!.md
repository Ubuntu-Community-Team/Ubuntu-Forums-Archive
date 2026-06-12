---
title: "GDM was messed up, now it is almost fixed!"
date: 2011-04-06
forum: General Help
---

### Post by Rytron on 2011-04-06
Hi.

Yesterday I installed Slim login manager via [http://ubuntuguide.net/customize-ubuntu10-0410-1011-04-login-screen-appearance-via-slim-login-manager/comment-page-1#comment-5627](http://ubuntuguide.net/customize-ubuntu10-0410-1011-04-login-screen-appearance-via-slim-login-manager/comment-page-1#comment-5627)
This did not work out well so I switched back to GDM and rebooted. Then my bootup hangs at the Ubuntu logo.

It is now almost fixed. I'm not certain as to what fixed it. It may have been these steps:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Add /usr/sbin/gdm to /etc/X11/default-display-manager

Now, when I get to login screen I get the change theme box (very odd). Is there a set routing to reset/reinstall all GDM data to default?

Thanks.

---

### Post by ~Plue on 2011-04-06
> **Rytron said:**
> 
Now, when I get to login screen I get the change theme box (very odd). Is there a set routing to reset/reinstall all GDM data to default?

if you purge and then reinstall gdm then it would probably reset to default

but in this case, purge might not work if you've manually made a link in gdm autostart directory. take look in** /usr/share/gdm/autostart/LoginWindow** and see if there are any links to the appearance properties dialog


hope this helps
-verbeck

---

### Post by Rytron on 2011-04-06
> **~Plue said:**
> if you purge and then reinstall gdm then it would probably reset to default

but in this case, purge might not work if you've manually made a link in gdm autostart directory. take look in** /usr/share/gdm/autostart/LoginWindow** and see if there are any links to the appearance properties dialog


hope this helps
-verbeck

Thank you ~Plue for solving another problem today. I went to [COLOR="Indigo"]/usr/share/gdm/autostart/LoginWindow[/COLOR] and deleted a link to 'Appearance Preferences'. How did that link get there though?

---

### Post by ~Plue on 2011-04-06
> **Rytron said:**
> Thank you ~Plue for solving another problem today. I went to [COLOR=Indigo]/usr/share/gdm/autostart/LoginWindow[/COLOR] and deleted a link to 'Appearance Preferences'. How did that link get there though?
you're welcome  :grin:

maybe you were customizing the gdm theme/appearance before installing slim?

---

