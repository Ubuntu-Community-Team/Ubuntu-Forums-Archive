---
title: "WikidPad Doesn't Render Graphviz"
date: 2012-03-06
forum: General Help
---

### Post by upandacross on 2012-03-06
Problem:
[INDENT]I am running  on Ubuntu 10.04 (/proc/version gives: "Linux version 2.6.32-39-generic")
I have Graphviz 2.2.0 installed successfully
I have WikidPad 2.1 installed as well.
In the WikidPad gui Extra->Options->Graphviz, I have set:[INDENT]Directory of Executables: /usr/bin
Name of dot executable: dot
Name of neato executable: neato
Name of twopi executable: twopi
Name of circo executable: circo
Name of fdp executable: fdp
[/INDENT]I created and saved a wiki document with the following text:[INDENT][:dot: digraph g { a->b }; noerror]
[/INDENT]When, in the WikidPad gui, I select Wiki->Print->Preview, I see the text, not a graph. No error messages, nothing in syslog.

Just to make sure, at a command prompt, I vi a file named t.dot with similar text ( "digraph g { a->b }" ), run dot -Tpdf t.dot, and open t.pdf successfully with the Document Viewer finding the directed graph as was exected.

Found nothing in a long google session.
[/INDENT]Please advise.

---

