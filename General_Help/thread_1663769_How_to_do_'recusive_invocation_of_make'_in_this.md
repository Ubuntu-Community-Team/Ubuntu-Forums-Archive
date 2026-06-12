---
title: "How to do 'recusive invocation of make' in this ?"
date: 2011-01-10
forum: General Help
---

### Post by van7hu on 2011-01-10
Suppose,I have a directory tree like this:
[PHP]
|-- makefile
|-- one
|   `-- makefile
`-- two
    `-- makefile
[/PHP]now, I want makefile in top folder to invoke makefile in folder 'one' and then 'two',how can I do that.
the content of top folder makefile as follow:
[PHP]
folders = one two
.PHONY: $(folders)
$(folders):
    $(MAKE) -C $@
[/PHP]but,it does not work !,it only invokes makefile in 'one' and not invoke makefile in 'two' folder.
notes: my purpose here is to recursively invoke make as many folders as specified in $(folders) (1,2 and more...)

---

