---
title: "Empathy and Pidgin invisibility"
date: 2010-07-31
forum: General Help
---

### Post by FreedomOverdose on 2010-07-31
Hello

I've tried both empathy and pidgin for gmail chat and facebook. ok, facebook doesn't have an invisibility mode, so none of them supports it. But what about gmail chat?? In empathy, I set my status as invisible and it switches to busy. In pidgin, it says I'm invisible, but other people can see me, and gmail says I'm NOT invisible! What's going on?! :S

Thanks

---

### Post by FreedomOverdose on 2010-08-03
bump! anyone please?

---

### Post by heiNey on 2010-08-03
did you try signing out of google chat in the browser and use only pidgin and set it invisible in pidgin?

---

### Post by FreedomOverdose on 2010-08-03
I'll try that out, but I think it's still the same... :(

---

### Post by heiNey on 2010-08-03
that's strange because i never log into the google chat in gmail and invisible works fine for me, with pidgin.  i dont use empathy so im not sure about that one.

EDIT: i retract my statement.  i remember it working before, but apparently it doesn't anymore.  sorry, im not sure why either.

---

### Post by FreedomOverdose on 2010-08-05
> **heiNey said:**
> that's strange because i never log into the google chat in gmail and invisible works fine for me, with pidgin.  i dont use empathy so im not sure about that one.

EDIT: i retract my statement.  i remember it working before, but apparently it doesn't anymore.  sorry, im not sure why either.

That's weird :S. So you're saying it worked before? :S

The main problem is that it tells you that you're invisible, but you're not!! :S

---

### Post by FreedomOverdose on 2010-08-08
bump!

---

### Post by gauravbutola on 2010-08-08
I can confirm this bug on empathy and everybody have the same problem with empathy that it sets status to busy instead of invisible.
sorry haven't used pidgin, cant comment on that. but for empathy its a 100% bug.

---

### Post by FreedomOverdose on 2010-08-08
the same for pidgin, it tells me it's "invisible" but my buddies see me as "busy"... the worst part is that pidgin won't even tell you your correct status :S

---

### Post by t.rei on 2010-08-09
The invisible status being borked for some time is one of the major gripes I have at the IM people currently.

Invisible should - according to me - be: online, but not displayed as such to anyone.

Invisible is - according to them - online, and still visible to everyone on my friendslist, but none of the ones that I don't have in my list.

My solution for that was: create a whole lot of seperate im addresses. :/

I miss working invisiblity.

---

### Post by FreedomOverdose on 2010-08-09
Actually, I *think* only Gmail is a problem. It works with WLM, right?

---

### Post by FreedomOverdose on 2010-08-14
anyone?? This is annoying :(

---

### Post by FreedomOverdose on 2010-08-17
I found a temporary fix on Pidgin: on the XMPP Console plugin (enable it) and type:

<presence>
<priority>5</priority>
</presence>
<presence type="unavailable">
<priority>5</priority>
</presence>

That should work most of the times (but not always!)

---

### Post by FreedomOverdose on 2010-08-18
It seems that there's some sort of "timeout". The trick above will keep you invisible for some time, but after that, you go back visible, and have to reapply the trick

---

### Post by karthick87 on 2010-10-06
> **FreedomOverdose said:**
> I found a temporary fix on Pidgin: on the XMPP Console plugin (enable it) and type:

<presence>
<priority>5</priority>
</presence>
<presence type="unavailable">
<priority>5</priority>
</presence>

That should work most of the times (but not always!)


Should i want to type the above  script all the time when i use pidgin.

---

### Post by FreedomOverdose on 2010-10-06
actually, I found a solution. the plugin GTalk Shared Status should do the trick :)

---

