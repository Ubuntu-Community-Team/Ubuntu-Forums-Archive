---
title: "HTML Rendering weirdness"
date: 2012-03-30
forum: General Help
---

### Post by prosmart on 2012-03-30
Greetings

Currently running stock Ubuntu 11.10 fully updated.

I noticed a week or so that some HTML emails I received were not rendering correctly. Particularly (but not limited to) notifications from Facebook. Some other emails I received earlier (and looked fine earlier) now had no text showing whatsoever unless I used "view body as simple HTML". I assumed it was a Thunderbird issue and tried a few changes, new account, reverted back to an older version etc. but all to no avail. Then I noticed that when using Firefox, I got exactly the same issues on some web pages. Rather than rendering correctly, often I would get some background panels with no graphics and almost always no text whatsoever. Some web sites that normally render in a single screen now were inordinately long. Tried switching email temporarily to Evolution and everything looked perfect. Switched browser back to Chrome and all looked fine again. The only commonality I can find is that the problem appears to be limited to Thunderbird and Firefox.

Tried the same programs on my daughter's machine running Ubuntu 10 and everything works perfectly.

Can anyone suggest where to start looking? I really don't want to switch email clients but I'm finding this really difficult to work with.

Any other info please let me know.

Thanks and Regards

Nigel.

---

### Post by Paddy Landau on 2012-03-31
Obviously the Mozilla engine is not working correctly. I am not sure how to find the problem, but there is one thing I know you can try.

Try a new profile. Close Firefox; delete the folder [FONT=Lucida Console]~/.mozilla[/FONT] (*warning:* you will lose all your Firefox settings, add-ons and bookmarks, so back them up first). Rerun Firefox and see whether or not this is fixed.

---

### Post by prosmart on 2012-03-31
> **Paddy Landau said:**
> Obviously the Mozilla engine is not working correctly. I am not sure how to find the problem, but there is one thing I know you can try.

Try a new profile. Close Firefox; delete the folder [FONT=Lucida Console]~/.mozilla[/FONT] (*warning:* you will lose all your Firefox settings, add-ons and bookmarks, so back them up first). Rerun Firefox and see whether or not this is fixed.

Hi Paddy. Thanks for the input and suggestions. Alas it was not a fix. Renamed my .mozilla folder and re-ran Firefox. Still got a window with most things missing. Have attached a sample to this post of the Facebook login page. It's got me b*gggered.

Nigel.

---

### Post by HiImTye on 2012-03-31
try
```
firefox --safe-mode
```
and resetting your profile

---

### Post by prosmart on 2012-03-31
> **HiImTye said:**
> try
```
firefox --safe-mode
```
and resetting your profile

Hi HiImTye

Tried that too. Attached is the result. I have also attached a screenshot of a facebook notification I received. Gets weirder and weirder. (BTW - It's not just facebook stuff. Gizmag newsletters have pictures but no text!).

Any other ideas? Are there any libraries or settings files that are shared between TBird and Firefox?

TIA

Nigel.

---

### Post by HiImTye on 2012-03-31
a forum suggested that the workaround is to start it with the environment variable MOZ_DISABLE_PANGO=1 for instance[FONT=monospace]:
[/FONT]```
MOZ_DISABLE_PANGO=1 firefox
```

---

### Post by prosmart on 2012-03-31
> **HiImTye said:**
> a forum suggested that the workaround is to start it with the environment variable MOZ_DISABLE_PANGO=1 for instance[FONT=monospace]:
[/FONT]```
MOZ_DISABLE_PANGO=1 firefox
```

Same thing I'm afraid. I did get this though - was getting it all the time but forgot to mention it.

```
(firefox:14259): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='IndicEngineFc', font='Tahoma 14.6669921875', text=' '
```

Nigel.

---

### Post by HiImTye on 2012-03-31
try changing your font

---

### Post by prosmart on 2012-03-31
> **prosmart said:**
> Same thing I'm afraid. I did get this though - was getting it all the time but forgot to mention it.

```
(firefox:14259): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='IndicEngineFc', font='Tahoma 14.6669921875', text=' '
```

Nigel.

I even tried (as suggested elsewhere) putting 

export MOZ_DISABLE_PANGO=1 in my .profile and logging out and in. Still the same old story.

I've attached another example. This is the start up screen from Thunderbird - proves at least that it is a software issue rather than bad html.

Nigel.

---

### Post by prosmart on 2012-03-31
> **HiImTye said:**
> try changing your font

You might be on to something here. I remember I did install a load of fonts onto the system just before this happened. I was looking for a nice handwriting font to write letters to my GF with.

Is there any sanity checking for fonts?

I just changed a few of the fonts I'm using in Edit>Preferences>Content>Fonts>Advanced and managed to have "some" effect - not what I wanted but something changed (a coloured bar on one of the web pages changed shape). It's a little odd though. I only made changes in Libre Office Writer.

Is there any way of sanity checking the fonts on the system?

Nigel.

---

### Post by prosmart on 2012-03-31
> **prosmart said:**
> You might be on to something here. I remember I did install a load of fonts onto the system just before this happened. I was looking for a nice handwriting font to write letters to my GF with.

Is there any sanity checking for fonts?

I just changed a few of the fonts I'm using in Edit>Preferences>Content>Fonts>Advanced and managed to have "some" effect - not what I wanted but something changed (a coloured bar on one of the web pages changed shape). It's a little odd though. I only made changes in Libre Office Writer.

Is there any way of sanity checking the fonts on the system?

Nigel.

Got it!

I remembered that I had installed all the ttf files from my old windoze box as well as the handwriting fonts. Obviously a MAJOR clash with some already existing fonts. <SLAP!>

Removed all the additional fonts I had installed, put in just the few I wanted and re-ran fc-cache -f -v.

Instant success.

Thanks so much to the responders - I really appreciate the pointers suggestions etc.

Cheers

Nigel.

---

