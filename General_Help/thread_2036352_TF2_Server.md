---
title: "TF2 Server"
date: 2012-08-01
forum: General Help
---

### Post by Criss969 on 2012-08-01
I am hosting a Team Fortress 2 server with Lubuntu and was wondering if there was any way I could make an executable launch file.

---

### Post by marinara on 2012-08-02
Just to keep it simple:

open up lxterminal and type this:```

leafpad runtf2
```then type something like this into leafpad:```

srcds_run -game tf -autoupdate -maxplayers 24 +map cp_badlands
```after you save the file, you can run the script in bash with the . command

so (don't type the $)```

$ . runtf2
```If you want more info, learn how to write a simple bash script.

---

### Post by Criss969 on 2012-08-08
> **marinara said:**
> Just to keep it simple:

open up lxterminal and type this:```

leafpad runtf2
```then type something like this into leafpad:```

srcds_run -game tf -autoupdate -maxplayers 24 +map cp_badlands
```after you save the file, you can run the script in bash with the . command

so (don't type the $)```

$ . runtf2
```If you want more info, learn how to write a simple bash script.

Thanks a lot for your help! :)

---

