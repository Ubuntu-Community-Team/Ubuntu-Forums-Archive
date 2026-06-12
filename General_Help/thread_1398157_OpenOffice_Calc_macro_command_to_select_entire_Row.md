---
title: "OpenOffice Calc: macro command to select entire Row/Column"
date: 2010-02-04
forum: General Help
---

### Post by chewearn on 2010-02-04
What is the macro command (in OpenOffice Basic) to select an entire Row or Column?

I tried to "Record Macro", then click on the Row/Column header, which would then select the entire row/column.  But "Record Macro" failed to capture this action.

---

Thank you for your kind assistance.

---

### Post by chewearn on 2010-02-05
bump (in the night)

---

### Post by juar1 on 2013-02-22
This code select an entire line up to column ac.
From there you can execute commands like dispatcher.executeDispatch(document, ".uno:ClearContents", "", 0, Array())

```

dim linha as integer
dim celula as string
document   = ThisComponent.CurrentController.Frame
dispatcher = createUnoService("com.sun.star.frame.DispatchHelper")
linha=2
dim args7(0) as new com.sun.star.beans.PropertyValue
args7(0).Name = "ToPoint"
'celula = "a"&linha&":ac"&linha 'gives error
celula = "a"&linha+":ac"&linha 'works right
args7(0).Value = celula
dispatcher.executeDispatch(document, ".uno:GoToCell", "", 0, args7())

```

There you go...

---

### Post by oldos2er on 2013-02-22
Old thread closed.

---

