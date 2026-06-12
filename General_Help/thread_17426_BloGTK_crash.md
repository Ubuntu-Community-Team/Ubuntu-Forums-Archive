---
title: "BloGTK crash"
date: 2005-02-28
forum: General Help
---

### Post by SickBoy on 2005-02-28
As soon as it starts BloGTK chashes with the followin message:

> Traceback (most recent call last):
  File "/usr/lib/blogtk/BloGTK.py", line 1230, in ?
    blogtk = BloGTK()
  File "/usr/lib/blogtk/BloGTK.py", line 133, in __init__
    self.grabConfig()
  File "/usr/lib/blogtk/BloGTK.py", line 421, in grabConfig
    self.rpcServer = proxy.get_xmlrpc_server(self.url)
  File "/usr/lib/blogtk/proxy.py", line 66, in get_xmlrpc_server
    return server(url)
  File "/usr/lib/python2.4/xmlrpclib.py", line 1357, in __init__
    raise IOError, "unsupported XML-RPC protocol"
IOError: unsupported XML-RPC protocol


Any ideas?

---

### Post by Deusiah on 2005-03-29
I have exactly the same problem. It seems to be permissions related. If you hit alt+f2 and type gksudo BloGTK it opens and is perfectly usable.

If I find out anything more I'll post here.

---

### Post by Deusiah on 2005-03-29
OK I have found out how to get BloGTK working again. After using it for a bit as root is wasn't long before it stopped working again.

That stuck me as odd so I immediatly thought config files! Delete .BloGTK in your home directory and BloGTK will load again.

I have found out what was causing the crash for me. When I tried to delete the default profile it would say I couldn't delete it but would delete it anyway. This was crashing the program for me.

I reccomend once you have your account details setup that you make a copy of the config file in .BloGTK so you can easily fix the problem incase it goes wrong again.

---

### Post by BloGTK on 2005-03-29
Interesting...

You shouldn't be able to delete the default account, but apparently the program still does it, which will cause problems with the configuration. I'll do some testing on it tonight to see if it's an issue with BloGTK (which appears to be the case.)

---

### Post by Deusiah on 2005-03-30
Are you the authour of BlogGTK? If so thanks for looking into this problem and thank you for making BloGTK.

If there's anything I can do to help just let me know, I can't program in Python but I can test the software to see if your fix corrects the issue.

---

### Post by trallali on 2005-10-27
Dear All,

the above mentioned hints helped me a lot starting BlogTK (1.0), connects to the server, but does not download articles or anything else from the blog. Uploading is fine.

The default user is set.

The link to my blog is: [http://sammelsurium.blogsport.de](http://sammelsurium.blogsport.de)

Then I typed my login and password in the form. And I chose "Meta API" as option.

My blog is a Word Press weblog, running on a Word Press-multiuser-server.

Here is, what the Terminal tells me:
(I don't know, what is important, so I post everything...)

```
/usr/bin/BloGTK:151: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.editPostsItem.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:201: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.toolbar1.set_tooltips(gtk.TRUE)
/usr/bin/BloGTK:202: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.toolbar2.set_tooltips(gtk.TRUE)
/usr/bin/BloGTK:222: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.treeView.set_headers_visible(gtk.TRUE)
/usr/bin/BloGTK:226: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  column.set_resizable(gtk.TRUE)
/usr/lib/blogtk/config.py:457: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.proxyButton_None.set_active(gtk.TRUE)
/usr/lib/blogtk/config.py:190: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.blogRadioMW.set_active(gtk.TRUE)
/usr/lib/blogtk/config.py:195: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.defaultPublishCheck.set_active(gtk.FALSE)
/usr/lib/blogtk/config.py:202: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.useUTF8Check.set_active(gtk.FALSE)
/usr/bin/BloGTK:53: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.postButton.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:57: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.titleEntry.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:64: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.recallMenuOption.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:66: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.titleEntry.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:67: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.extendedView.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:68: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.excerptView.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:69: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.commentsCheck.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:70: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.pingsCheck.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:71: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.breaksCheck.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:72: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.keywordEntry.set_sensitive(gtk.FALSE)
/usr/bin/BloGTK:73: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.trackbackEntry.set_sensitive(gtk.FALSE)
/usr/lib/blogtk/config.py:282: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.blogRadioMT.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:284: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.blogRadioBlogger.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:286: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.blogRadioMW.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:293: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.defaultPublishCheck.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:298: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.defaultMainCheck.set_active(gtk.FALSE)
/usr/lib/blogtk/config.py:300: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.useUTF8Check.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:468: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.proxyButton_System.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:470: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.proxyButton_Custom.get_active() == gtk.TRUE:
/usr/lib/blogtk/config.py:472: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  if self.proxyButton_None.get_active() == gtk.TRUE:
/usr/bin/BloGTK:505: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.postButton.set_sensitive(gtk.TRUE)
/usr/bin/BloGTK:506: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.editPostsItem.set_sensitive(gtk.TRUE)
/usr/bin/BloGTK:530: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.titleEntry.set_sensitive(gtk.TRUE)
/usr/bin/BloGTK:531: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.extendedView.set_sensitive(gtk.TRUE)
/usr/bin/BloGTK:532: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.excerptView.set_sensitive(gtk.TRUE)
/usr/bin/BloGTK:537: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.recallMenuOption.set_sensitive(gtk.TRUE)
BloGTK could not read the response from the server. Try limiting the amount
of retrieved entries or check to make sure your posts contain valid XML
Traceback (most recent call last):
  File "/usr/lib/blogtk/config.py", line 192, in fillForm
    if self.defaultPublish == "1":
AttributeError: blogtkPrefs instance has no attribute 'defaultPublish'
/usr/lib/blogtk/config.py:188: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.blogRadioBlogger.set_active(gtk.TRUE)
Traceback (most recent call last):
  File "/usr/lib/blogtk/config.py", line 192, in fillForm
    if self.defaultPublish == "1":
AttributeError: blogtkPrefs instance has no attribute 'defaultPublish'
Traceback (most recent call last):
  File "/usr/lib/blogtk/config.py", line 192, in fillForm
    if self.defaultPublish == "1":
AttributeError: blogtkPrefs instance has no attribute 'defaultPublish'
Traceback (most recent call last):
  File "/usr/bin/BloGTK", line 491, in getBlogs
    self.grabConfig()
  File "/usr/bin/BloGTK", line 421, in grabConfig
    self.rpcServer = proxy.get_xmlrpc_server(self.url)
  File "/usr/lib/blogtk/proxy.py", line 66, in get_xmlrpc_server
    return server(url)
  File "/usr/lib/python2.4/xmlrpclib.py", line 1357, in __init__
    raise IOError, "unsupported XML-RPC protocol"
IOError: unsupported XML-RPC protocol
Traceback (most recent call last):
  File "/usr/bin/BloGTK", line 491, in getBlogs
    self.grabConfig()
  File "/usr/bin/BloGTK", line 421, in grabConfig
    self.rpcServer = proxy.get_xmlrpc_server(self.url)
  File "/usr/lib/blogtk/proxy.py", line 66, in get_xmlrpc_server
    return server(url)
  File "/usr/lib/python2.4/xmlrpclib.py", line 1357, in __init__
    raise IOError, "unsupported XML-RPC protocol"
IOError: unsupported XML-RPC protocol


```

Thank you in advance, and please apologize my bad English and me being newbie to Linux and Ubuntu...

---

