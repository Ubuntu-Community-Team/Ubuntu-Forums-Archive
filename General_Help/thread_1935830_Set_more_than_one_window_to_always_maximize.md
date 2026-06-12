---
title: "Set more than one window to always maximize"
date: 2012-03-05
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-05
I'm trying to set a couple of my apps (terminal and update manager) to always launch maximized. I'm doing it through CCSM > Window Management > Window Rules > Maximized. Now, it's working okay if I put in only one window there, but if I try to add another, the setting is lost for both. For example, this works fine:

[IMG]http://files.myopera.com/tomica/files/ccsm_maximized_1.png[/IMG]

But this doesn't:

[IMG]http://files.myopera.com/tomica/files/ccsm_maximized_2.png[/IMG]

I'm using the 20.04b1, don't know if that matters.

---

### Post by gldearman on 2012-03-06
I believe that ccsm interprets "&" as AND, meaning a window would have to meet **both** criteria to be maximized.  No window is named both "gnome-terminal" **and** "update-manager."

Try substituting "|" instead of "&."  I'm pretty sure ccsm reads "|" as OR.

i.e.,
```
name=gnome-terminal | name=update-manager
```

Hope that helps.

---

### Post by HiImTye on 2012-03-06
> **&#1058 said:**
> I'm trying to set a couple of my apps (terminal and update manager) to always launch maximized. I'm doing it through CCSM > Window Management > Window Rules > Maximized. Now, it's working okay if I put in only one window there, but if I try to add another, the setting is lost for both. For example, this works fine:

[IMG]http://files.myopera.com/tomica/files/ccsm_maximized_1.png[/IMG]

But this doesn't:

[IMG]http://files.myopera.com/tomica/files/ccsm_maximized_2.png[/IMG]

I'm using the 20.04b1, don't know if that matters.

just hit the 'add' or '+' or w/e on the side, it will set the syntax for you

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-06
> **HiImTye said:**
> just hit the 'add' or '+' or w/e on the side, it will set the syntax for you
That's exactly how I was doing it. CCSM adds & when you use the + button.

In any case gldearman's advice worked. Thanks a lot! This setting maximizes both Terminal and Update Manager:

```
name=gnome-terminal | name=update-manager
```

---

