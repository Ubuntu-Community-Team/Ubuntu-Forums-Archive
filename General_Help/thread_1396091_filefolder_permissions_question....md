---
title: "file/folder permissions question..."
date: 2010-02-01
forum: General Help
---

### Post by blur xc on 2010-02-01
Example- you have three groups of people that need different levels of access to a set of files and folder.  Group A has no access.  No reading, no writing.  Group B is to have read only access.  Group C has read/write access.  How do you do that in Linux?

I'm askign hypothetically, btw...  I don't have a current need to set up anything this way, but at my last job we had that kind of setup for our engineering folders.  Members of the engineering group, engineers, designers, drafters and document control personnel had read write access to the engineering files, cad drawings, models, pdf's, etc...  Manufacturing and purchasing had read only access.  They needed the drawings for inspecting incoming parts, manufacturing parts, and sending drawings to vendors to have parts made.  Everyone else in the company had no access.

In linux, as I understand it, you can make an engineering group owner of the files in the folder, and make the engineers members of the engineering group, with fill read/write access.  Then the best you could do is give the 'others' read only access.

Would you need to make two groups, and give the parent directory say a doc_control group with read only access, and others to have no permissions to the folder?

Anyway- just thinking...  maybe I'll mess around on my VM with some of these combinations.

Thanks,
BM

---

### Post by chewearn on 2010-02-02
1. Change files and folders permission to 750 and 640.

2. Set file and folders owner+group to C.

2. Since group C is the owner, it has read/write access.

3. Add group B to group C.  This gives group B read access.

4. Since group A is not part of group C, it has no access.

---

