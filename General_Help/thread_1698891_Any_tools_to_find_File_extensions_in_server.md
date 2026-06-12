---
title: "Any tools to find File extensions in server"
date: 2011-03-02
forum: General Help
---

### Post by vishnube on 2011-03-02
Hi , 

I am doing a migration and where i face problem with few file formats . I have the list of acceptable file formats , now i need to find the rest of the file formats other than the acceptable file formats. is there any tool available for this ?
 or can some give me the VBA macro ..

My VBA macro works to find the file extension in a particular folder but the problem is its ending when the count increases to 65000 (excel limit). 
How do i use If condition here to avoid the acceptable format and give me unique file formats .

Please help..

Sub getFileextension()
Dim ws As Worksheet
Dim count, i As Long
Dim varTemp As Variant

Set ws = Application.ActiveSheet
count = ws.UsedRange.Rows.count

For i = 3 To count
    varTemp = Split(ws.Cells(i, 1).Value, ".")
    ws.Cells(i, 3).Value = varTemp(UBound(varTemp))
Next
End Sub

---

### Post by asmoore82 on 2011-03-02
Welcome,

This is primarily a support forum for [Ubuntu]("http://www.ubuntu.com/") [Linux]("http://en.wikipedia.org/wiki/Linux").

What are you talking about?

---

