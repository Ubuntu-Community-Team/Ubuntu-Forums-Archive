---
title: "Geany code snippets"
date: 2010-03-09
forum: General Help
---

### Post by uShafee on 2010-03-09
Hai. It says in the geany documentation that i can specify multiple cursor positions. But after i define a snippet like that - lets say for example:

```

for=for ($i = 0; $i < %cursor%; $i++){ %cursor% }

```

it only takes me to the first cursor point. A second tab results in a regular tab being inserted into the code.. What am i doing wrong?

---

### Post by aldolat on 2010-11-04
You have to define a keybinding in Geany preferences: go to the tab Keybinding / Editor section and press "Change" button. Press the combination you want and save. Now you can use this feature.

---

