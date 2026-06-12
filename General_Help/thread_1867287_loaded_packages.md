---
title: "loaded packages"
date: 2011-10-22
forum: General Help
---

### Post by ggumas on 2011-10-22
Does some one know how I can  go about getting a list of all the packages installed on my computer.
and if I have tist is there a simple way to load the paackages into a second computer.
Thanks for any help or suggestions
George

---

### Post by crazy bird on 2011-10-22
> **ggumas said:**
> Does some one know how I can  go about getting a list of all the packages installed on my computer.
and if I have tist is there a simple way to load the paackages into a second computer.
Thanks for any help or suggestions
George

i think this command will help you. In a terminal type this command:
```
dpkg --get-selections
```

---

### Post by drs305 on 2011-10-22
If you are more comfortable with a GUI app and your version of Lubuntu has Synaptic, you can generate a list of packages.

Open Synaptic. File, Save Markings As. Select a name and make sure to tick the 'Save full state' checkbox. Save the file and copy it to the new computer.

On the new computer, File, Read Markings, and open the same file to incorporate the list of installed files.

---

### Post by ggumas on 2011-10-23
> **drs305 said:**
> If you are more comfortable with a GUI app and your version of Lubuntu has Synaptic, you can generate a list of packages.

Open Synaptic. File, Save Markings As. Select a name and make sure to tick the 'Save full state' checkbox. Save the file and copy it to the new computer.

On the new computer, File, Read Markings, and open the same file to incorporate the list of installed files.
Thanks for the help
george

---

