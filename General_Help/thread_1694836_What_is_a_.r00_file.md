---
title: "What is a .r00 file?"
date: 2011-02-24
forum: General Help
---

### Post by kooley on 2011-02-24
hello, i have recently downloaded a few files containing .r00 files and i was wonder what are they? one file in question has .r00-.r79 its supposed to be an instructional video dvd.

i need to know what to do with these files and what they are.

thank you.

---

### Post by Telengard C64 on 2011-02-24
They might be members of a RAR multi-volume archive. If so you may extract them using command line RAR or WinRar.

---

### Post by kooley on 2011-02-24
ohh ok and how would i go about using the command line RAR? as wine on my comp is messed up so winrar isnt an option

---

### Post by polardude1983 on 2011-02-24
Just put this command in the terminal to install unrar

```
sudo apt-get install unrar
```

Then open it and extract the files inside

---

### Post by Telengard C64 on 2011-02-25
I believe you need to install the non-free unrar package. Then open a terminal window and navigate to the directory containing the .r## files. The command below will extract the archive, assuming all volume members are present.

```
unrar x filename.r00
```

---

### Post by kooley on 2011-02-25
thank you for the suggestions

---

