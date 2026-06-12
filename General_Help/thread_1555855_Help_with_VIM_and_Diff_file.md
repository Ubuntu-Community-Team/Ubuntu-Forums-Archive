---
title: "Help with VIM and Diff file"
date: 2010-08-18
forum: General Help
---

### Post by Epifrin on 2010-08-18
I was following a tutorial on how to set xmpp. When I came to the step where I'm supposed to modify a file using a text editor. The tutorial states this command:

```
$> sudo vim /etc/ejabberd/ejabberd.cfg
```

And gives the diff file, which is the analysis of changes made to the original file I understand. It goes as such:

```
diff --git a/ejabberd/ejabberd.cfg b/ejabberd/ejabberd.cfg
index b5ab8a0..129abda 100644
--- a/ejabberd/ejabberd.cfg
+++ b/ejabberd/ejabberd.cfg
@@ -185,11 +185,10 @@
   %%              ]},

   {5280, ejabberd_http, [
-           http_poll,
+            http_bind,
             web_admin
                         ]}
   ]}. etc. etc.
```

My question is, how can I apply the changes while having the diff that compares the original and modified versions of the file (ejabberd.cfg here)? Thanks in advance.

---

### Post by DaithiF on 2010-08-18
Hi,
i'm not sure what you're asking -- do you need help using vim to make that change to the file, or are you asking how you can view both the diff file and the file you are editing at the same time?

if you are new to vim and just want to get this one quick change made you might find it easier to use an editor like gedit instead.  that will give you a graphical editor with menus, scrollbar, etc.
```
gksudo gedit /etc/ejabberd/ejabberd.cfg
```

you can open multiple files in gedit, so to view the diffs file just do file->open from the menu.

[SIZE=1](for what its worth, i'm not bashing vim here, its actually my favourite application of all time.  but it has a learning curve.)
[/SIZE]

---

