---
title: "How to display all/hidden characters in gedit text editor?"
date: 2009-12-09
forum: General Help
---

### Post by prestonkredlon on 2009-12-09
Can i display all/hidden characters, like CR LF, in **gedit **text editor? 

If yes, how? 

If not, which text editor is capable of displaying all characters?

Thanks for the help in advance.

---

### Post by Phyds on 2010-09-07
I was looking for the same thing as you today but found no answers after Googling a lot. Most people suggest to use **vim**, which I love too, but I wanted something integrated with **gedit**.

Fortunately, there is one plugin that can show some hidden characters. Install the **gedit-plugins** package from the official Ubuntu repositories, and activate and configure the plugin *Draw Spaces* in **gedit** preferences. It is made to show spaces, but you can show tabs and newlines characters. For newlines, however, it doesn't distinguish between LF only, CR only or CR+LF newlines, they appear all the same. Anyway you can specify which to use when saving a file with **gedit**.

---

