---
title: "Evolution Won't Start"
date: 2010-01-27
forum: General Help
---

### Post by jdorenbush on 2010-01-27
Don't know what is going on here, but Evolution won't start. I've tried reinstalling. When I click the icon to open it, the little loading cursor displays for a few seconds then it disappears and nothing else happens.

Any ideas?

---

### Post by mvalviar on 2010-01-27
Try this on the terminal ```
evolution --force-shutdown
```

If it doesn't work try renaming your ~/.evolution folder to something like bak.evolution.

---

### Post by jdorenbush on 2010-01-27
> **mvalviar said:**
> Try this on the terminal ```
evolution --force-shutdown
```

If it doesn't work try renaming your ~/.evolution folder to something like bak.evolution.

```
evolution --force-shutdown
evolution: error while loading shared libraries: libgdata-google-1.2.so.1: cannot open shared object file: No such file or directory
```

Renaming .evolution folder didn't work either. :(

---

### Post by audiomick on 2010-01-27
Does the same error show up with just
```
evolution
```
in the terminal?
This command should start the program, the one you just tried should force a shutdown if there is an instance that is "hung up".

The error message looks like a missing depenancy, i.e. a library the program is trying to access and can't.

---

### Post by jdorenbush on 2010-01-27
Same error message...

I searched Synaptic, the only thing I could find similar was "libgdata-google1.2-dev". I installed that, but that didn't seem to fix anything.

I couldn't find: "libgdata-google-1.2.so.1" in Synaptic.

---

### Post by audiomick on 2010-01-27
Your evolution setup is in a hidden file in your home folder called .mozilla, if I remember rightly.

You could try backing that up and re-installing.

I have to go to bed now. I'll look back in here tomorrow.
good luck.

---

### Post by jdorenbush on 2010-01-28
> **audiomick said:**
> Your evolution setup is in a hidden file in your home folder called .mozilla, if I remember rightly.

You could try backing that up and re-installing.

I have to go to bed now. I'll look back in here tomorrow.
good luck.

I didn't see anything in there... :\

---

### Post by audiomick on 2010-01-28
Sorry, my mistake. I obviously should have been in bed already...:redface:
The .mozilla one is Firefox. Evolution stores to .evolution

Have a look for that.

---

### Post by jdorenbush on 2010-01-28
> **audiomick said:**
> Sorry, my mistake. I obviously should have been in bed already...:redface:
The .mozilla one is Firefox. Evolution stores to .evolution

Have a look for that.

Tried that. Didn't work. :(

---

### Post by audiomick on 2010-01-28
> **jdorenbush said:**
> Tried that. Didn't work. :(

What didn't work. You couldn't find the .evolution folder, or re-installing didn't change anything?

edit: I just looked back to your first post; you had already tried re-installing, hadn't you.
Have to think about it some more...:(

---

### Post by jdorenbush on 2010-01-28
> **audiomick said:**
> What didn't work. You couldn't find the .evolution folder, or re-installing didn't change anything?

edit: I just looked back to your first post; you had already tried re-installing, hadn't you.
Have to think about it some more...:(

Yeah, I've tried removing the folder and reinstalling. Didn't work. Thanks for trying here. Let me know if you come up with any other ideas.

---

