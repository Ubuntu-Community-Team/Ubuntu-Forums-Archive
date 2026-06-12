---
title: "Conky date display: automatically change days of week"
date: 2011-01-02
forum: General Help
---

### Post by begtognen on 2011-01-02
I'd like to tweak my Conky so it automatically displays the days of the week correctly. So for example, if TODAY were Tuesday, it would look like this:

Tuesday

Wednesday

Thursday

Friday

[etc.]

And then tomorrow, *automatically*, it would look like this:

Wednesday

Thursday

Friday

[etc.]

I know I can get it to display *today's* date like this:

${time %A}

But how do I get it to display tomorrow's date?

Thanks so much for any help/suggestions.

---

### Post by stinkeye on 2011-01-02
Terminal commands:

today
```
date +%A
```

Tomorrow```
date -d +1day +%A
```

Day after tomorrow```
date -d +2days +%A
```

etc, etc


In conky 
```
${execi 3600 date +%A}
${execi 3600 date -d +1day +%A}
${execi 3600 date -d +2days +%A}
${execi 3600 date -d +3days +%A}
${execi 3600 date -d +4days +%A}
${execi 3600 date -d +5days +%A}
${execi 3600 date -d +6days +%A}
```

---

