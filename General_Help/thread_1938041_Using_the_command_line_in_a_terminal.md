---
title: "Using the command line in a terminal"
date: 2012-03-09
forum: General Help
---

### Post by seastick on 2012-03-09
Is it possible to switch workspace from a terminal - ie using the command line?  If so how?
And if this can be done, is it then possible to start an application on a specific (different) workspace from the command line?

Ubuntu 10.04 LTS

Many thanks for any feedback.

---

### Post by papibe on 2012-03-09
Hi seastick.

You can fake a keyboard event using 'xdotool'. If you create the event that is link to change workspaces, you'll change as if the keys were pressed.

For instance, this moves me to the workspace to the right:
```
xdotool key "ctrl+alt+Right"
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by Bonster on 2012-03-10
With compiz place window plugin, u can do that, otherwise might checkout gdevilspie

---

### Post by seastick on 2012-03-12
Thanks for the tips; I'll have a play and let you know how it goes.
Cheers

---

### Post by sudodus on 2012-03-12
> **papibe said:**
> Hi seastick.

You can fake a keyboard event using 'xdotool'. If you create the event that is link to change workspaces, you'll change as if the keys were pressed.

For instance, this moves me to the workspace to the right:
```
xdotool key "ctrl+alt+Right"
```Hope that helps, and tell us how it goes.
Regards.
Thanks for a valuable tip :KS

---

