---
title: "Can't install Aquaria and Penumbra"
date: 2010-05-07
forum: General Help
---

### Post by jorrieboy on 2010-05-07
I have bought the Humble Indie Bundle, so also Aquaria and Penumbra. 

When i run "./aquaria-lnx-humble-bundle.mojo.run", it loads the installer window, but after a while it reports that there is an fatal error, and that he can't make a file.

With Penumbra (it's an .sh file), the terminal reports this:
"Can't open Penumbra_overture_1.1.sh"

Can someone please help me?!?!

EDIT:
I have installed Penumbra now, but it crashes right after the story if i begin a new game...

I've also downloaded aquaria again, and i've installed it now

---

### Post by ssj6akshat on 2010-05-09
You need to give the sh executable permissions by going into the terminal and typing

chmod a+x <drag the sh here>

enjoy and thanks for supporting the Humble Indie Bundle

---

### Post by ssj6akshat on 2010-05-09
Oh no Double Post,sorry my Internet connection was having problems.

---

### Post by themusicalduck on 2010-05-09
Right click on Applications at the top left and Edit Menus. Find Penumbra under the Games menu, and click properties. Copy the text in the Command: box.

For me it's /usr/games/PenumbraCollection/Overture/penumbra, but it depends where you installed it.

Type that into a terminal and hit enter, then see if you get an error message when it crashes.

---

