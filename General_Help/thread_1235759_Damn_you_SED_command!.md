---
title: "Damn you SED command!"
date: 2009-08-09
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-09
What's Up?

OK, So Yet again I've fell into SED's trap special set for me. For my latest improvement for my project I need to be able to replace the text "</b>" with nothing, but its that dam "/" that throws SED off course, Anyone know a way around this?

Thanks Bye.

---

### Post by j.bell730 on 2009-08-09
Instead of "</b>", try "<\/b>".

---

### Post by Chamillionaire2 on 2009-08-09
> **j.bell730 said:**
> Instead of "</b>", try "<\/b>".

Thanks but i get this?

```
sed "s/<\/b>///" Output.txt >> Output.txt
sed: -e expression #1, char 10: unknown option to `s'

```

---

### Post by j.bell730 on 2009-08-09
Try this instead:
```
sed "s#<\/b>##" Output.txt >> Output.txt
```

Hope that helps.

---

### Post by adrianx on 2009-08-09
> **Chamillionaire2 said:**
> Thanks but i get this?

```
sed "s/<\/b>//**[COLOR=Red]/[/COLOR]**" Output.txt >> Output.txt
sed: -e expression #1, char 10: unknown option to `s'

```

You have one too many '/'

Try:
```
sed 's/<\/b>//'
```

---

### Post by Chamillionaire2 on 2009-08-09
Strange, They both seem to work but after running the command, SED uses alot of CPU, i left the pc for about 15 mins and upon coming back it was still running trying to do whatever it was trying to do. 

Killall sorted it out but after trying to view the text file it must have been corrupted by sed. Its probley because the text file may be too big, ill have to section it into small chunks.

Thanks Bye.

---

