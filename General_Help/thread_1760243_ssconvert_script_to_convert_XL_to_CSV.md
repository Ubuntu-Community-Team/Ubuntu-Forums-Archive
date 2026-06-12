---
title: "ssconvert script to convert XL to CSV"
date: 2011-05-16
forum: General Help
---

### Post by LASTGUY2GETPS2 on 2011-05-16
Hey all so I have a folder containing many subfolders of XL files. I could use a little help making an ubuntu script.

Specifically I want a script that scans this folder and every subfolders for anything with a "xl" extension "*.xl" and convert it to a CSV file via 

```
ssconvert *.xl *.csv
```

I assume I need something like:

```
#!/bin/bash

/F %%a in ('dir /b /R *.xl') do  ssconvert %%a.xl %%a.csv
```

But I have no idea...

---

