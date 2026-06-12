---
title: "Can't add more than four keyboard layouts"
date: 2010-02-26
forum: General Help
---

### Post by scottiw2000 on 2010-02-26
I work in a lot of different languages that use different fonts (Greek, Hebrew, Syriac, Ethiopic, etc.). I have added four keyboard layouts under Keyboard Preferences > Layouts. But now the "Add" button is grayed out. Is there a limit on the number of layouts you can have active? If so, is there any way to get around this? It's a real pain if I have to add and remove layouts all the time, especially because I'm sometimes testing new custom layouts as well.

Thanks in advance.

---

### Post by simosx on 2010-03-02
> **scottiw2000 said:**
> I work in a lot of different languages that use different fonts (Greek, Hebrew, Syriac, Ethiopic, etc.). I have added four keyboard layouts under Keyboard Preferences > Layouts. But now the "Add" button is grayed out. Is there a limit on the number of layouts you can have active? If so, is there any way to get around this? It's a real pain if I have to add and remove layouts all the time, especially because I'm sometimes testing new custom layouts as well.

Thanks in advance.

Yes, there is currently a limit :(.

A workaround would be to enable keyboard shortcuts that would execute a special command to switch to a particular keyboard layout.

Therefore
1. Go to System/Preferences/Keyboard shortcuts
2. Add the first new custom shortcut, let's say "US English", with command 'setxkbmap us'. Then, once you OK it, set the shortcut to Ctrl-F1.
3. Then, add "Greek', with command 'setxkbmap gr', shortcut Ctrl-F2.
4. You can add more layouts, etc. Look into /usr/share/X11/xkb/symbols/ for the correct layout file (like 'us', 'gr'). Search the net for more information on how to select a layout 'variant'.

You then switch with Ctrl+F1, Ctrl+F2, etc.

(For Greek, the default layout 'gr' works for Greek Polytonic as well, [http://simos.info/blog/archives/888](http://simos.info/blog/archives/888)).

---

### Post by AcIDx0 on 2010-03-06
Have the same problem exactly. Found this thread. 

I haven't really expected such a thing from such a liberal platform! Why is there a limitation of 4 layouts??!? This is really unexpected stupid limitation! I can  compare it only IPhone one not having A2DP whenit was default on every other phone.

Anyone cares to explain the logic behind such a limitation?

---

### Post by rcbinwi on 2010-03-11
Does anyone know how to change the default Syriac font?  The font looks strange.  Another problem is it won't produce connecting letters.  For example, there is only a final n, and no initial or medial.  Any ideas?

---

### Post by simosx on 2010-03-12
> **rcbinwi said:**
> Does anyone know how to change the default Syriac font?  The font looks strange.  Another problem is it won't produce connecting letters.  For example, there is only a final n, and no initial or medial.  Any ideas?

That's a polite question. Even off-topic, I'll venture an answer.

1. You set the UI font at System/Preferences/Appearance/Fonts
You can use TTF or OpenType fonts for this. Specifically in OpenOffice, you can use OpenType fonts if you get OpenOffice 3.2. Otherwise, try a Truetype font.

2. The Syriac keyboard layout is at /usr/share/X11/xkb/symbols/sy
It is possible it is not optimal, as it requires Syrian speakers to contribute their expertise.
To be able to display properly joined Syriac letters, the 'Pango' library uses a special module, /usr/lib/pango/1.6.0/modules/pango-syriac-fc.so
As far as I know, I am in the impression that this module works OK. You can search for 'pango syriac' for possible clues.

Do Syriac webpages in Firefox look OK? Apart from OpenOffice, try 'gedit' (the Text Editor in Accessories).

---

### Post by rcbinwi on 2010-03-12
Thank you for the response.  My apologies.  I was just happy to have the Syriac folks' attention.

I'll start a new thread.  Some other, related questions occurred to me.

---

### Post by santq on 2010-04-14
Really, why there is such limit? People run away from Windows to open source because they hate stupid limits like these.

Kind of funny that you can run Linux kernel with thousands of processors, but the most popular distro supports only four keyboard layouts. I don't mean to be impolite, I'm just looking for some rational for this.

---

### Post by scottiw2000 on 2010-04-19
Thanks simosx for the workaround. I'll try it. But I agree that this arbitrary limit is a problem. I'm going to post a suggestion elsewhere that they work on changing this.

---

### Post by simosx on 2010-04-20
> **scottiw2000 said:**
> Thanks simosx for the workaround. I'll try it. But I agree that this arbitrary limit is a problem. I'm going to post a suggestion elsewhere that they work on changing this.

The component in X.Org that deals with keyboard layouts is called XKB. There is an effort to revamp it with XKB2, however it is not released yet. I do not know if XKB2 fixes the number of layouts issue.

Is XKB that bad? Actually, XKB is technically really good and supports amazing things not available in other systems. The issue is that when it was written in the 90s by Sun engineers, there was little community involvement, the initial maintainers changed jobs, etc. The effort with XKB2 is to make XKB more manageable and simpler. Thus, if someone complains about XKB not being good, they are just being silly.

It is possible for the keyboard switching applet to bypass this limitation? As far as I know, this is what they are doing in KDE3 (no idea about KDE4). It is not rocket science, but I presume it makes the code messy. 

If you want to take this forward, the person to ask is Sergey Udaltsov. You can file a bug report at [https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd](https://bugzilla.gnome.org/browse.cgi?product=libgnomekbd)
which is the library for keyboard layout stuff in GNOME.
I remember vaguely the issue being discussed, though I cannot remember the explanation.

---

### Post by ambeginnersearchinginfo on 2010-10-28
I have also the problem with this limit and found this thread.
I am using Kubuntu 10.04 or 10.10  live system CD or DVD and there are two questions concerning your proposition.
When I am switching off and on the computer, I have to renew 
all tese commands. Is there any autoexec file or something like that which is executed
automatically once everytime the system is started, where I could put these commands
and how they would look like in such an autoexec file?
Can I exchange the function of the F1 and the Ctrl-F1 etc. by a command which I can put in the autoexec file, so I can change languages by just using the keys F1, F2, F3 and so on and using the F1-function etc. by the short cut Ctrl-F1 etc., because I almost do not use F1, F2" etc. but change the languages all the time and how would such a command look like?
Thank you.

---

### Post by buntuyu on 2011-04-13
Hi, I just thought I'd beat this drum a little, too.

Also, offer my perhaps less-than expert take on it

Not to overstate the obvious (for the veterans), but, just in case a new comer is reading:

As far as I understand, Linux (/Unix) is inherently a multi-tasking, multi-user, multi-processor, multi-EVERYTHING system. In theory, in practice, in spirit and in flesh... linux software development, AFAICT, has long been manifesting this fundamental notion of no-petty-limits on any type of multiples...

I see the gnome-keyboard-layout limitation of four layouts to be extremely odd and at odds with Linux philosophy. Would you agree?

I would guess it is the result of some quirk in the development process way back when.

Also, I would think that the fix should not be that laborious: To alter code so that it handles multiplicity instead of a singularity (an array versus a scalar) could be justifiably laborious.

But to simply extend an array that is already in place (provided in the code) allowing it to hold more elements, seems like a trivial matter.

I have not taken a look at the code, not being versed in C/C++. 

Has anyone out there given it a go?

Has anyone appealed directly to the developers?

It does seem very frustrating not to have the liberty to add, say, 15 distinct layouts...

TIA

---

### Post by Vaphell on 2011-04-14
as it was explained in this thread, it's not gnome team's fault. It's a legacy of design decisions made by X developers years years ago (you know, X - that thing on top of which all graphical interfaces are done). They hardcoded 2 bits for layout-id (which allows 4 different values) or something.
Problem with legacy stuff which is very widespread is that it's hard to fix the problem without breaking lots of things - backwards compatibility is a bitch. Of course i agree it should be fixed but maybe developers think that the problem touches maybe few percent of users and they have more important issues.
It's very similar to the ungodly old restriction of 4 primary partitions that often makes it a pain to easily set up multisystem machines (especially on laptops with premade multiple primary partitions in place).

---

### Post by Krytarik on 2011-04-14
You may take a look at my earlier post on how to workaround that restriction:
[http://ubuntuforums.org/showthread.php?p=10333055#post10333055](http://ubuntuforums.org/showthread.php?p=10333055#post10333055)

Maybe it is finally of use for someone. ;)

Greetings.

---

### Post by MarkieB on 2011-06-26
no longer participating in ubuntuforums.org

---

### Post by redscorp on 2013-01-02
> **Vaphell said:**
> as it was explained in this thread, it's not gnome team's fault. It's a legacy of design decisions made by X developers years years ago (you know, X - that thing on top of which all graphical interfaces are done). They hardcoded 2 bits for layout-id (which allows 4 different values) or something.
Problem with legacy stuff which is very widespread is that it's hard to fix the problem without breaking lots of things - backwards compatibility is a bitch...

If it's really as you said (2 bits and stuff) then it's ugly.. I remember these times when such "optimizations" were common not only in embedded world but also in server OSes. So I can imagine why it (the limitation) is there and why it's so hard to cleanup this sh#t.

In my case I need 6 languages - damn this globalization, communication, internalization, etc. - to be smart is sooo troublesome sometimes. :lolflag: Can someone check/proof/ask if this nice 4-language limitation will be fixed in mentioned earlier next reincarnation of XKB? And if yes, when it will be added to common distros like ubuntu & Co.

PS: How boooooring. Even M$ Gameloader(tm) can handle more languages pretty good... I hope it will be fixed soon.

PPS: What alternatives to X with its infrastructure can be used now? I've heard about some substitution called Wayland or so. Can it handle more languages?

---

### Post by oldos2er on 2013-01-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

