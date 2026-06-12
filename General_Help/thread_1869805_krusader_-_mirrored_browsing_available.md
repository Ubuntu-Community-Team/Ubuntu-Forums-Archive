---
title: "krusader - mirrored browsing available?"
date: 2011-10-26
forum: General Help
---

### Post by antiplex on 2011-10-26
dear community,

i stubled over the nicht split-pane file-manager krusader very recently (can't believe it took that long since i've been looking for such for quite some time... *sigh*) and get to learn new useful features step by step.

one thing that i would consider very helpful and which i could not find in krusader yet is what the somewhat similar m$-software xplorer² calls mirror-browsing.
what mirror-browsing does is (if activated) to synchonise the two panels in a way that if i navigate into a directory in the active panel named 'abc' and there is a directory with the same name on the inactive panel, this inactive panels also follows into its own directory 'abc'. same applies if navigating out of a directory.
i found such functionality very helpful when comparing/manually updating folder structures and content and would be surprised if krusader does not offer such feature.
could somebody more krusader-experienced maybe give me a hint how this might be done?

or is there a completely different solution? i am aware of the synchronization-tool available within krusader, this is working well but i would very much welcome to have the described funtionality available as well. 

many thanks in advance,
anti

---

### Post by gsmanners on 2011-10-26
This sounds to me like a casual manual way of doing a diff. I don't suppose you've checked kdiff3? I'm sure that can probably even integrate with krusader (although don't ask me how as I haven't used krusader in years).

---

### Post by antiplex on 2011-10-26
hi gsmanners,

you are right, kdiff3 integrates nicely into krusader but that is not really what i need i believe. basically i would like the two panes of krusader to follow one another when navigating through directories that exist in both views.
of course what i would like to achieve through this is some sort of manual diff, but a listing of differences like the ones kdiff3 or meld provide do not really help me here.

hmm, i thought i may just have missed some option within krusader but of course maybe this is entirely inexistant...

---

### Post by gsmanners on 2011-10-26
That is a pretty esoteric feature. On its site, it says:

> Compare and synchronize folders

In dual pane mode xplorer² can show the contents of 2 folders in a single window, ideal for comparing and synchronizing content. Using scrap containers you can compare folder hierarchies, too.

I'm not sure what use it has for you, but it sounds to me like it was designed to be a lot like rsync or diff.

---

### Post by antiplex on 2011-10-27
hi gsmanners,

the mirrored-browsing feature of xplorer² is demonstrated [here]("http://zabkat.com/blog/wink/sync1.htm") until about the middle of the video. the flat-bowing-comparison is not directly part of what i meant.

i was hoping such a feature would exist in krusader already since both filemanagers seem to suit many similar needs and thought i might just have to know the name of this in krusader.

regards,
anti

---

