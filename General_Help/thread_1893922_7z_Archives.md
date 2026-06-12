---
title: "7z Archives"
date: 2011-12-11
forum: General Help
---

### Post by Kodeine on 2011-12-11
Salutations!

So I have several large 7z archives to which I am needing to decompress. On my old computer you would only need to highlight them all and select extract here from the right click menu. However such does not exist on my new computer. I've installed the p7zip module and although I can open the first archive (there naming scheme is <NAME>.7z.001, <NAME>.7z.002 etc) the others don't open as they give me a 'archive type not supported' message.

How can I unarchive all these?

---

### Post by mutley89 on 2011-12-11
Are they one archive split into several pieces? If so try this:
```
cat NAME.7z.* > NAME.7z
7z x NAME.7z
```

---

### Post by Kodeine on 2011-12-11
> **mutley89 said:**
> Are they one archive split into several pieces? If so try this:
```
cat NAME.7z.* > NAME.7z
7z x NAME.7z
```

Ah yes merging them all in to one works. Thought archive manager would just know they were all split files and work accordingly. Thanks

---

