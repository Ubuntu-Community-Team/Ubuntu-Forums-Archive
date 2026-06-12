---
title: "Banshee: Changing music folder location. Can I keep my ratings, etc?"
date: 2009-11-24
forum: General Help
---

### Post by nortexoid on 2009-11-24
I currently have all my music sitting on an NTFS windows partition that I'm going to get rid of. If I do and, retaining the folder structure, move it over to a EXT4 file system in Ubuntu (e.g. in my home Music folder), is there any way for Banshee to remember all my ratings, etc?

I fear that once I move my music, load up Banshee and import the new music folder, Banshee will think it's all new and erase the customized data I have. Anyone try this?

---

### Post by blazemore on 2009-11-24
If you open up the Banshee settings, you'll see an option for Write Metadata to Files.
This will write things like ratings to the files themselves, although I'm unsure if it will work for tracks you rated *before* you ticked this option.

---

### Post by nortexoid on 2009-11-24
Most of my stuff has been rated before the latest builds of Banshee that now come with this feature.

---

