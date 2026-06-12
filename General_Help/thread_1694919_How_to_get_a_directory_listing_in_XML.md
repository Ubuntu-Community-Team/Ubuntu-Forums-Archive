---
title: "How to get a directory listing in XML"
date: 2011-02-25
forum: General Help
---

### Post by Zakhafr on 2011-02-25
Hi,

would there be out there a program like **ls **that could produce an XML output of directories/files instead of a plain text output.

I could imagine something like

```
$ ls-xml
<list>
  <dir>
    <name>foo</name>
    <creation-date>2011-02-12T09:50:52+0100</creation-date>
    <content>
      <file>
        <name>bar</name>
 <!-- ... -->
      </file>
    </content>
  </dir>
</list>
```

---

