---
title: "Login screen Layout problem"
date: 2009-10-07
forum: General Help
---

### Post by karthikeyanbe442 on 2009-10-07
Can anybody tell me, how to change the keyboard layout to English while login to UBUNTU 9.04. 
I have made a mistake by choosing Tamil as my default keyboard layout. When i type my username and password it types in Tamil.
Please help me....

&#2965;&#3006;&#2992;&#3021;&#2980;&#3021;&#2980;&#3007;&#2965;&#3015;&#2991;&#2985;&#3021; &#2951;&#2995;&#2984;&#3007;&#2994;&#3016; &#2980;&#2965;&#2997;&#2994;&#3021; &#2980;&#3018;&#2996;&#3007;&#2994;&#3021;&#2984;&#3009;&#2975;&#3021;&#2986;&#2990;&#3021;
 [email]anusefulblog@wordpress.com[/email]

---

### Post by screaminfakah on 2009-10-07
When you first boot the computer in the Grub menu go to Recovery.  From there you can drop to the shell prompt

```
sudo dpkg-reconfigure xserver-xorg
```

This will let you change your keyboard setup.

---

### Post by karthikeyanbe442 on 2009-10-08
Thanks for your reply.
But i found a new way of solving this.

Quote:
1.booted the ubuntu in live session
2.accessed the console-setup file from the live session
  by using the command 
  Code:
  sudo gedit /media/disk/etc/default/console-setup
3.in that i made the changes as follows,
  Quote:
# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
4. then i restarted the system. Now the problem is solved and English is set as Default Keyboard layout.

Thanks once again

&#2965;&#3006;&#2992;&#3021;&#2980;&#3021;&#2980;&#3007;&#2965;&#3015;&#2991;&#2985;&#3021; &#2951;&#2995;&#2984;&#3007;&#2994;&#3016; &#2980;&#2965;&#2997;&#2994;&#3021; &#2980;&#3018;&#2996;&#3007;&#2994;&#3021;&#2984;&#3009;&#2975;&#3021;&#2986;&#2990;&#3021;
[email]anusefulblog@wordpress.com[/email]

---

### Post by karthikeyanbe442 on 2009-10-08
Thanks for your reply.
But i found a new way of solving this.

1.booted the ubuntu in live session
2.accessed the console-setup file from the live session
  by using the command 
  ```
sudo gedit /media/disk/etc/default/console-setup
```
3.in that i made the changes as follows,
> # The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
4. then i restarted the system. Now the problem is solved and English is set as Default Keyboard layout.

Thanks once again

&#2965;&#3006;&#2992;&#3021;&#2980;&#3021;&#2980;&#3007;&#2965;&#3015;&#2991;&#2985;&#3021; &#2951;&#2995;&#2984;&#3007;&#2994;&#3016; &#2980;&#2965;&#2997;&#2994;&#3021; &#2980;&#3018;&#2996;&#3007;&#2994;&#3021;&#2984;&#3009;&#2975;&#3021;&#2986;&#2990;&#3021;
[email]anusefulblog@wordpress.com[/email]

---

