---
title: "watch, tail, &amp; grep with colours for matching text"
date: 2009-12-14
forum: General Help
---

### Post by MaindotC on 2009-12-14
I monitor user logins on my machines - just to know who's using what - and I'd like to use the following command but have coloured or highlighted text matching my search string:
```

watch -n 2 'less .gvfs/sftp\ for\ user1\ on\ 192.168.1.111/var/log/auth.log | grep --color=auto -e user1 -e user2 -e user3 -e user4'

```

Just to explain my command here - I have the machine I'm watching mounted via sftp and I've found that those mounted areas are listed under .gvfs.  So, I'm using the watch command to check /var/log/auth.log file every 2 seconds, and I'm having that file tailed so I see the most recent entries, and then I grep those entries for specific users.  I have no idea if this is an efficient means of monitoring user logins so if you have any different suggestions I welcome them.

This command works fine, but I'd like the user names matching the search text to be coloured, or even varying colours if possible, to differentiate them from the usual text.  I've used the following command for grep to enable colours:
```

export GREP_COLOR='00;38;5;226'

``` which I found [here](http://www.debian-administration.org/article/grep_highlighting_matches_in_color) and turned on 256 colour matching anytime I use grep.  Then, I found that I can use:
```

tail .gvfs/sftp\ for\ user1\ on\ 192.168.1.111/var/log/auth.log | grep user1

```
and it does return coloured output for text that matched my query.  But once I throw in the "watch" command to make it real-time grepping, it drops the colour usage.

Can someone advise how I keep colour showing?

---

### Post by HyperFlexed on 2010-05-11
Although much later, I'd also like an answer to this one. Watch is awesome, but it could do with some pizzazz.

---

### Post by rnerwein on 2010-05-11
hi
have a look at the tail command: e.g. tail -f /var/log/auth.log | bla blu ...
then you will get every change immediately.
ciao

---

### Post by MaindotC on 2010-05-11
Ha - I am so glad I keep my subscriptions.  I actually forgot my watch command :D Thanks for replying lol

---

### Post by kwd on 2011-02-20
MaindotC

Hi 

A couple of things you said I am not clear about:

I use Xterm and it does not do 256 colors.  Are you using Eterm?

Did exporting GREP_COLOR='00;38;5;226' make each match a different color?

If not I can tell you how to do that if you are still interested.

kwd

---

### Post by MaindotC on 2011-02-21
Well right now I'm using Gnome Shell (even though it says Terminal) and bash - haven't tried xterm.

---

### Post by kwd on 2011-02-22
Thanks I will test the gnome shell. 

What about questions  1 and 2  ?

1 - Did exporting GREP_COLOR='00;38;5;226' make each match a different color?

2 - If it did not make each match, a different color, do you still want to know how to do that? I can tell you how if you are interested.

---

