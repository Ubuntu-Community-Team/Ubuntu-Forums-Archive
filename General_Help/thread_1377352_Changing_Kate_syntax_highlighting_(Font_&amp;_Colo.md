---
title: "Changing Kate syntax highlighting (Font &amp; Colors schema)"
date: 2010-01-10
forum: General Help
---

### Post by nortexoid on 2010-01-10
I'm using a dark theme (Obsidian Coast) which is making things a pain to read using the default LaTeX syntax highlighting and color schema of Kate. I can edit the schema just fine, but that does not affect the colors of certain highlighting features, such as the color of expressions which fill in the ellipses of "\section{...}", which turn out black or "\begin{...}" which turn out dark blue.

Is there any way to fine-tune the highlighting features of a particular kind of markup (LaTeX in my case)?

---

### Post by rCXer on 2010-01-10
You have to edit the kate's syntax highlighting.  In Ubuntu the files are located at **/usr/share/kde4/apps/katepart/syntax/**.  I don't know where they are in kubuntu.  According to [kate's website]("http://kate-editor.org/article/writing_a_kate_highlighting_xml_file") it should be located in **$KDEDIR/share/apps/katepart/syntax**,  If $KDEDIR is empty just run...
```

kde-config --prefix

```

You should open a file called latex.xml in the directory. For example if you want to change the color of begin, look at line ~8 you should see...
```
 <RegExpr String="\\begin(?=[^a-zA-Z])" attribute="Structure" context="FindEnvironment" beginRegion="block" />
```

You'll notice that the **attribute="Structure"**.  Near the bottom (~line 428 ) of the file you should see an itemData whose **name="Structure"**...
```
<itemData name="Structure" defStyleNum="dsNormal" color="#F00000" selColor="#80FFD0" bold="0" italic="0"/>
```...and  notice the **color="#F00000"**.  Change the color's value to whatever you want to.

---

### Post by nortexoid on 2010-01-10
Thanks very much. The folder location is the same (usr/share/...) in Kubuntu. (The location ~/.kde/share/apps/katepart exists but is empty.) Now it's just a matter of editing the latex.xml and replacing all dark colors with something appropriate.

Thanks again!

---

### Post by GameManK on 2010-01-10
> **nortexoid said:**
> Thanks very much. The folder location is the same (usr/share/...) in Kubuntu. (The location ~/.kde/share/apps/katepart exists but is empty.) Now it's just a matter of editing the latex.xml and replacing all dark colors with something appropriate.

Thanks again!
I think you can copy the latex.xml to the ~/.kde/share/apps/katepart directory and edit it there, and kate will use that version.  That way you don't need to edit the system version and don't need sudo to do it.

---

### Post by nortexoid on 2010-01-10
> **GameManK said:**
> I think you can copy the latex.xml to the ~/.kde/share/apps/katepart directory and edit it there, and kate will use that version.  That way you don't need to edit the system version and don't need sudo to do it.

That worked like a charm. I placed a copy of /usr/share/kde4/apps/katepart/syntax/latex.xml in ~/.kde/share/apps/katepart/syntax/ and then edited it exactly as I wanted.

Thanks again.

---

### Post by nortexoid on 2010-05-29
> **rCXer said:**
> You have to edit the kate's syntax highlighting.  In Ubuntu the files are located at **/usr/share/kde4/apps/katepart/syntax/**.  I don't know where they are in kubuntu.  According to [kate's website]("http://kate-editor.org/article/writing_a_kate_highlighting_xml_file") it should be located in **$KDEDIR/share/apps/katepart/syntax**,  If $KDEDIR is empty just run...
```

kde-config --prefix

```

You should open a file called latex.xml in the directory. For example if you want to change the color of begin, look at line ~8 you should see...
```
 <RegExpr String="\\begin(?=[^a-zA-Z])" attribute="Structure" context="FindEnvironment" beginRegion="block" />
```

You'll notice that the **attribute="Structure"**.  Near the bottom (~line 428 ) of the file you should see an itemData whose **name="Structure"**...
```
<itemData name="Structure" defStyleNum="dsNormal" color="#F00000" selColor="#80FFD0" bold="0" italic="0"/>
```...and  notice the **color="#F00000"**.  Change the color's value to whatever you want to.

So actually that didn't quite work. The problem is that the the the stuff in certain command options is very dark blue or black. E.g. in \begin{proof}, 'proof' is dark blue. And in \section{Introduction}, 'Introduction' is black. There doesn't seem to be anything in the default latex.xml file that allows one to change this. Is there something under <itemDatas> I can add to adjust those colors?

---

