---
title: "Lucid-Thunderbird can not be set as default for FF &quot;Send link&quot;!"
date: 2010-05-14
forum: General Help
---

### Post by emarkay on 2010-05-14
I tried both  FF Preferences > Applications > Content Type and 
Ubuntu > Preferences > Preferred Applications > Mail Reader

This in an updated Lucid 32 bit Intel install - nothing beyond a few Synaptic additions and a few Synaptic deletions. This is a real PITA recently,  since a few more adds/deletes (Surely Evolution is not needed to get TB to work in FF???). 

I know a bit about all this but is there a dependency / application I have removed (without notice (Grrrr!)), or something else?

Thanks!

---

### Post by dcstar on 2010-05-14
> **emarkay said:**
> I tried both  FF Preferences > Applications > Content Type and 
Ubuntu > Preferences > Preferred Applications > Mail Reader

This in an updated Lucid 32 bit Intel install - nothing beyond a few Synaptic additions and a few Synaptic deletions. This is a real PITA recently,  since a few more adds/deletes (Surely Evolution is not needed to get TB to work in FF???). 

I know a bit about all this but is there a dependency / application I have removed (without notice (Grrrr!)), or something else?

Thanks!

Install the galternatives package and check any relevant setting there, and the Gconf configuration editor may also have a setting.

---

### Post by emarkay on 2010-05-15
Did that and looked there and nothing about "firefox" or "mozilla firefox" appear in the first or in any of the "apps" in the latter.

This is becoming a real PITA - anyone have any other ideas??

---

### Post by DougieFresh4U on 2010-05-17
Having near same issue
When ever I open email and click link in email that SHOULD trigger Firefox to open, I get the 'Launch Application' box

---

### Post by emarkay on 2010-05-17
> **DougieFresh4U said:**
> Having near same issue
When ever I open email and click link in email that SHOULD trigger Firefox to open, I get the 'Launch Application' box


You have nothing selected - see "preferred Applications", and confirm what's there for "Mail Reader".  I think that's your issue.

Mine has "Thunderbird" both as a a link and an app.  Neither work.

Was going to do a reinstall anyway as this is an original Alpha test install - gotta clear out the kibble-N-[mega]bits...  :)

---

### Post by DougieFresh4U on 2010-05-17
> **emarkay said:**
> You have nothing selected - see "preferred Applications", and confirm what's there for "Mail Reader".  I think that's your issue.

Mine has "Thunderbird" both as a a link and an app.  Neither work.

Was going to do a reinstall anyway as this is an original Alpha test install - gotta clear out the kibble-N-[mega]bits...  :)

I do have Thunderbird in Preferred Applications and still the Launch Application thingy opens.
Thanks

---

### Post by emarkay on 2010-05-17
Aha!  Apparmor!!!

Changed "enforce" to "complain".

Email again! 

Now removing that profile for good!

---

