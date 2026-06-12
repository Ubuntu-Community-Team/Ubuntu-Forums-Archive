---
title: "Boost or amplify speakers"
date: 2009-10-12
forum: General Help
---

### Post by YMS_1975 on 2009-10-12
I was wondering if there's any sort of application that will boost my speaker volume.

I've read through some of the posts on this forum, as it appears I'm not the only one experiencing issues with sound while using Ubuntu 9.04 on a laptop and I've tried the suggestions posted there, but none of them seemed to work.

So, all I'd like to know is if there is a software solution for this mild annoyance. FYI, I did experience this problem with Windows as well (however not to this degree). I could live with it in Windows, but in Ubuntu it seems to be much worst.

Anyhoo...I'd like to have this fixed, but if there's no fix for it I might just settle on buying a USB powered external speakers (specifically, the Logitech V20's).

So, I ask : **Is there software that will boost or amplify my speakers volume?**

---

### Post by OpenGuard on 2009-10-12
alsamixer ( PCM )

---

### Post by YMS_1975 on 2009-10-12
> **OpenGuard said:**
> alsamixer ( PCM )

Thanks for your prompt reply.

There is two programs that come up when I search for this software : 

1) Alsamixergui
2) GNOME ALSA Mixer

Which one specifically, would you recommend?

---

### Post by OpenGuard on 2009-10-12
> **YMS_1975 said:**
> Thanks for your prompt reply.

There is two programs that come up when I search for this software : 

1) Alsamixergui
2) GNOME ALSA Mixer

Which one specifically, would you recommend?

None of them ( as I've used only CLI version ). Simply enter alsamixer in Terminal ( it's already installed ) and use arrow keys to navigate through the mixer window and pull things up/down.

---

### Post by YMS_1975 on 2009-10-12
> **OpenGuard said:**
> None of them ( as I've used only CLI version ). Simply enter alsamixer in Terminal ( it's already installed ) and use arrow keys to navigate through the mixer window and pull things up/down.


Fair enough. 

But after using that, it shows that everything is at 100%, so there's no way to boost it or amplify the existing settings?

---

### Post by OpenGuard on 2009-10-12
> **YMS_1975 said:**
> Fair enough. 

But after using that, it shows that everything is at 100%, so there's no way to boost it or amplify the existing settings?

I don't think that there's a way to boost it more than that, tough, I might be wrong ( there is always someone who've found a workaround :D ).

---

### Post by YMS_1975 on 2009-10-12
> **OpenGuard said:**
> I don't think that there's a way to boost it more than that, tough, I might be wrong ( there is always someone who've found a workaround :D ).

I hope so. I don't want to buy external speakers because then my laptop will be more bulkier.   :(

---

### Post by blackened on 2009-10-12
> **YMS_1975 said:**
> I hope so. I don't want to buy external speakers because then my laptop will be more bulkier.   :(

VLC has a built-in software pre-amp that will let you crank the volume up to 400%, but, because it's software based, can have the side effect of making the audio sound like crap.

Instead of the external speakers, I would suggest you invest in a nice pair of headphones.

---

### Post by YMS_1975 on 2009-10-12
> **blackened said:**
> VLC has a built-in software pre-amp that will let you crank the volume up to 400%, but, because it's software based, can have the side effect of making the audio sound like crap.

Instead of the external speakers, I would suggest you invest in a nice pair of headphones.

Nice idea, but the problem is many times my wife will sit next to me and we'll watch something on YouTube together, so that can be a problem. As a matter of fact, she & I were just watching something earlier today, and she was a little unimpressed by the performance of the speakers, which is what prompted my post.  :) 
Also, VLC would not allow me to crank up the volume on streaming videos; only downloaded materials and/or CD/DVD media (at least, to the best of my knowledge).

I've tried VLC so I know about that software (one of the best media players out there).

---

### Post by blackened on 2009-10-12
I've always found the performance of built-in laptop speakers to be lackluster to say the very least, so I can't say that I find your problem surprising. Really the only good solution would be to get some external speakers as you mentioned. 

If you're absolutely bent on getting something that is USB powered (without an AC adapter) then don't expect stellar performance. 5 volts doesn't drive much, especially in the bass range.

As an alternative, Philips (and surely others) makes a model that can use either AC or batteries for that little bit of extra power. The V20s you mentioned have also gotten decent reviews.

---

