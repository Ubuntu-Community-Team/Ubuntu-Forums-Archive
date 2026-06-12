---
title: "Synergy: mouse trapped in client screen"
date: 2009-11-14
forum: General Help
---

### Post by blue4paper on 2009-11-14
Well, I've got synergy up and running fine, except for 1 problem: once i drag my mouse over from my server machine (windows) into my laptop/client machine (ubuntu) the mouse is trapped and I have to close to the connection to bring the pointer back to windows.

Here's my config file. I was thinking I might need to add an extra option or something to allow the mouse to switch screens.

> section: screens
        mycomputer:
        laptop123:
end
section: links
        mycomputer:
                right = laptop123
        laptop123:
                left = mycomputer

end

---

### Post by Brandon Williams on 2009-11-15
Have you tried running both synergyc and synergys with the -f option in order to get debugging output? And are both of the screen names resolvable hostnames on both machines?

---

