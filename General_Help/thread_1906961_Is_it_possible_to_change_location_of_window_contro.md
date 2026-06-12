---
title: "Is it possible to change location of window control buttons?"
date: 2012-01-10
forum: General Help
---

### Post by arroy_0209 on 2012-01-10
I am using ubuntu 10.04 LTS and the default appearance preference is set to "ambiance" where the control buttons (minimizing, maximizing, killing an window, like firefox) is located at the top left corner. Is it possible to change the location of these three buttons to the right top corner in "ambiance" mode? I want to customize in all windows like firefox, terminal etc.

---

### Post by Karlchen on 2012-01-10
Hello, arroy_0209.

Launch **gconf-editor**. Navigate to **apps** => **metacity** => **general**. In the right-hand pane locate the parameter string **button_layout**.
By default it will read: **close, minimize, maximize**. Change it to read **menu:minimize, maximize,close**
That's it. Each window will instantly display the old layout known from Karmic Koala and - ehem - Windows.
In case you do not wish to display the menu button in the top left corner, change the parameter button_layout to read **:minimize, maximize,close**
Note the colon at the beginning. Everything left of the colon will appear in the top left corner, everything right of the colon will appear in the top right corner.

Kind regards,
Karl

---

