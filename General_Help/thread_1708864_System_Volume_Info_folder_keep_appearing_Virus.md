---
title: "System Volume Info folder keep appearing? Virus?"
date: 2011-03-17
forum: General Help
---

### Post by crimsiris on 2011-03-17
Hello!

I am a new user of Linux and it was just my luck that my Windows partition along with my WD 350GB external HDD got infected with a virus. My computer science buddies suspect that the virus in my HDD was in a folder called System Volume Information. 

Right now, my Windows partition's been removed so my netbook is 100% Linux. I also deleted said folder from my HDD. However, the System Volume Information folder in my HDD still keeps on appearing.

I read that the System Volume Information folder is a Windows folder so I'm wondering why it still keeps on appearing? Is this still the virus? I'm skeptical but right now, I really don't know.

I'd appreciate any help I can get..

---

### Post by seawolf167 on 2011-03-17
The System Volume Information folder is a hidden folder that Windows uses to store it's System Restore information and restore points. 

If you don't have Windows anymore you can safely remove this folder.

The only problem is that this folder is a protected Windows folder on an NTFS formatted partition. The only way to remove this folder permanently is to reformat the drive.

---

