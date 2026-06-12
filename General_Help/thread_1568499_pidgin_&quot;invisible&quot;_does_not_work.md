---
title: "pidgin &quot;invisible&quot; does not work"
date: 2010-09-05
forum: General Help
---

### Post by tubunu on 2010-09-05
Is there any workaround for Pidgin's "invisible" not working? If I go "invisible" others (on Yahoo accounts) still can see me online, which is pointless, really. I don't have anything checked under Presence settings, so why is invisible VISIBLE? Thanks for any insight.

---

### Post by tubunu on 2010-09-08
I found out that I had enabled psychic mode under Plugins, but now that I disabled it, my contacts can still see me even though Pidgin's set to "invisible" mode by default and I never switch to "Available". Would anyone be willing to shed some light on this? Thanks.

---

### Post by mastablasta on 2010-09-08
have you tried reinstalling Pidgin? remove, purge and install again.

---

### Post by pbrane on 2010-09-08
I don't think all protocols support "invisibility". And it may be that Pidgin doesn't support invisible on some protocols that do. I know that Yahoo has changed some of their protocol stuff in the past and it can take awhile for Pidgin to catch up. At least the pidgin version in the repos.

---

### Post by tubunu on 2010-09-10
> **pbrane said:**
> I don't think all protocols support "invisibility". And it may be that Pidgin doesn't support invisible on some protocols that do. I know that Yahoo has changed some of their protocol stuff in the past and it can take awhile for Pidgin to catch up. At least the pidgin version in the repos.

Right, thanks. I think this makes sense.

---

### Post by Gunman1982 on 2010-09-10
You could check the pidgin.im webpage, maybe there is already a ticket about that.

---

### Post by karthick87 on 2010-10-06
1. Open the Buddy List.
2. In the menu, Tools->Plugins. Enable XMMP Console. Close the Plugin Window
3. In the menu again, Tools->XMMP Console->XMMP Console.
(See if your account in which you want to go invisible is selected if you have multiple accounts. )
4. In the text box, put the following XML snippet
{{{
<presence>
<priority>5</priority>
</presence>
<presence type="unavailable">
<priority>5</priority>
</presence>
}}}
and then press enter.

---

