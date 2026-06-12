---
title: "Firefox - One Instance"
date: 2010-01-30
forum: General Help
---

### Post by joeknoodle on 2010-01-30
I remember I used to be able to prevent Firefox from opening a new instance, but I can't remember how. 

How do you configure Firefox to only allow one instance?

---

### Post by warfacegod on 2010-01-30
Do you mean opening links in new windows?

Go to: Edit> Preferences> Tabs tab

---

### Post by joeknoodle on 2010-01-31
I'm talking about having only one firefox open at a time. It's not about the tabs, but the application itself.

---

### Post by lovinglinux on 2010-01-31
> **joeknoodle said:**
> I'm talking about having only one firefox open at a time. It's not about the tabs, but the application itself.

That's the normal behavior. Unless you add *-no-remote* to your launchers. So whenever you click the Firefox launcher it will open a new window using the same profile, not a new instance of Firefox. If that is not what is happening, then you need to check you launchers commands.

---

### Post by warfacegod on 2010-01-31
lovinglinux, your link still doesn't want to open.

---

### Post by lovinglinux on 2010-01-31
> **warfacegod said:**
> lovinglinux, your link still doesn't want to open.

Weird, It's working fine here. Can you ping it? the ip is 64.79.79.227

---

### Post by warfacegod on 2010-01-31
> **lovinglinux said:**
> Weird, It's working fine here. Can you ping it? the ip is 64.79.79.227

10 Packets Transmitted

0 Received

---

### Post by lovinglinux on 2010-01-31
> **warfacegod said:**
> 10 Packets Transmitted

0 Received

Try tracerout to see where the communication stops.

---

### Post by warfacegod on 2010-01-31
If you want the top of the list, let me know.

---

### Post by lovinglinux on 2010-01-31
> **warfacegod said:**
> If you want the top of the list, let me know.

[This proxy](http://flyproxy.com/nph-proxy.pl/) should work.

---

### Post by kaibob on 2010-01-31
I think the answer to the OP's question varies, depending on what he wants to happen when he starts firefox more than one. If he wants a new tab to be created in the existing firefox window, then a change of about:config settings will work. I haven't tried them, but I think the correct settings are those shown in the post referenced below. If the OP wants to be notified that firefox is already running or if he wants the operating system to change focus to the existing firefox window, then I believe he has to run firefox from a shell script.

A few additional thoughts. Compiz seems to do a lot of things that metacity won't do, so perhaps Compiz has a way to do what the OP wants.

I seem to recall that the Tab Mix Plus extension can be set to force firefox to start by creating a new tab in an already-running firefox window. I can't find anything on this right now, but it might be something to look into.

I agree with lovinglinux that the default firefox laucher starts a new window if firefox is already running and not a new instance of firefox. I tested this by clicking four times on the default firefox launcher. Four firefox windows were created and the taskbar contains four firefox buttons, but the top and pgrep commands only show one firefox.

REFERENCE:

> To perform the ultimate lock on Firefox into opening everything in one window in tabs, open about:config and set the following prefs:
browser.link.open_external set to 3 (should already be)
browser.link.open_newwindow to 3
browser.link.open_newwindow.restriction to 0 (zero)
To avoid your window resizing you need to restrict javascript from resizing windows. Go to:
Tools > Options > Content > Enable JavaScript > Advanced button > Allow scripts to: > [ ] Move or resize existing windows
Make sure that item is UNchecked. (Click the box to clear the checkmark, if present.)

[http://forums.mozillazine.org/viewto...st=0&sk=t&sd=a](http://forums.mozillazine.org/viewto...st=0&sk=t&sd=a)

---

### Post by lovinglinux on 2010-01-31
> **kaibob said:**
> I seem to recall that the Tab Mix Plus extension can be set to force firefox to start by creating a new tab in an already-running firefox window. I can't find anything on this right now, but it might be something to look into.

[All-in-one](https://addons.mozilla.org/en-US/firefox/addon/1027) sidebar can do that.

---

### Post by warfacegod on 2010-01-31
Just at a cursory perusal, I like the setup. Nicely organized, and much more pleasing to the eye. So far, I like it allot.

Interestingly, I used your Fly Proxy link earlier and got no farther than there. Now, Fly Proxy won't open but your direct link will.](*,)

---

