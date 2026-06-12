---
title: "Terminal Help"
date: 2010-10-25
forum: General Help
---

### Post by Crizzie on 2010-10-25
Hi,

I'm trying to figure out how to create a shortcut icon that's able to open a terminal and run these two commands for me. However, the only downside is that the terminal has to stay open.. it can't close.

```

cd ./srcds/orangebox/
./srcds_run -console -game cstrike +map de_dust2 -maxplayers 16
```

How could I accomplish this?

Thanks,
Criz

---

### Post by AlphaLexman on 2010-10-25
Put an ampersand after the command. It will run in the background.
```
cd ./srcds/orangebox/
./srcds_run -console -game cstrike +map de_dust2 -maxplayers 16 &
```

---

### Post by Crizzie on 2010-10-25
AlphaLexman,

I'm not wanting to run in the background. I'm using it for script development and I need to watch the console output. It's just that I don't know how to take those commands and compile them into an icon/shortcut that will allow me to double click it and have those commands ran.

---

### Post by AlphaLexman on 2010-10-25
Make it an executable bash script.

---

### Post by Crizzie on 2010-10-25
> **AlphaLexman said:**
> Make it an executable bash script.

I'm not quite sure how to do that.. I'm pretty new to Ubuntu.

---

### Post by AlphaLexman on 2010-10-25
```
#!/bin/bash
cd ./srcds/orangebox/
./srcds_run -console -game cstrike +map de_dust2 -maxplayers 16 &
```Copy the above Code to a file (gedit maybe), save it to your Desktop, in a terminal, **ch**ange the **mod**ification to make it e**x**ecutable:
```
chmod +x filename_you_saved_it_as
```then you should be able to double click it.

---

