---
title: "Open shell script with..?"
date: 2011-04-23
forum: General Help
---

### Post by RobotGymnast on 2011-04-23
My shell scripts recently stopped working (Under Gnome) when I double-clicked them. Running them from command prompt works fine, so I suspect they're not opening with the right application - How do I reset how shell scripts open? Opening with bash doesn't seem to help, nor opening with gnome-terminal.

---

### Post by user333 on 2011-04-23
You might have to right-click the script, go to the permissions tab, and click "allow to run as program"

---

### Post by RobotGymnast on 2011-04-23
> **user333 said:**
> You might have to right-click the script, go to the permissions tab, and click "allow to run as program"

Just checked - the permissions are still fine. As I say, they worked up until I turned on the computer today.

---

### Post by user333 on 2011-04-23
Ok. Try this: go to the open-with tab, and select gnome-terminal.

---

### Post by RobotGymnast on 2011-04-23
> **user333 said:**
> Ok. Try this: go to the open-with tab, and select gnome-terminal.

No "gnome-terminal" option (I installed from a minimal build), but entering the custom command gnome-terminal simply causes terminal to open. Entering as a custom command "gnome-terminal -x" causes a window to briefly open, then die. Running the script from an existing terminal works fine.

---

### Post by user333 on 2011-04-23
That's strange. I'll try to figure out something else.

---

### Post by user333 on 2011-04-23
Try adding a custom application, and use "sh" as the command. Then right-click and select open with->sh

You can do the same with bash too, if it's a bash script.

---

### Post by RobotGymnast on 2011-04-23
> **user333 said:**
> Try adding a custom application, and use "sh" as the command. Then right-click and select open with->sh

You can do the same with bash too, if it's a bash script.

Same results - terminal window pops up for a split second, then disappears. Running through bash or sh from an existing terminal works fine.

---

### Post by Vaphell on 2011-04-23
wait, isn't that normal that terminal window closes as soon as the script ends (can be split second if script is not long)?
put **read** at the end and see if terminal stays waiting for user input.

---

### Post by RobotGymnast on 2011-04-23
> **Vaphell said:**
> wait, isn't that normal that terminal window closes as soon as the script ends (can be split second if script is not long)?
put **read** at the end and see if terminal stays waiting for user input.

Ordinarily, yes, but these scripts are essentially just wrappers for other programs (in this case, a Minecraft server & client), which stay open indefinitely until the right input is received.

---

### Post by RobotGymnast on 2011-04-23
They started working again, all of a sudden. I can't remember making any changes to anything either..

---

### Post by RobotGymnast on 2011-04-24
And stopped working again..
Edit: And started again (again) all of a sudden..

---

