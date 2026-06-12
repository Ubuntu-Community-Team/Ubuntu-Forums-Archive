---
title: "Compiling Audacity for gtk2 support"
date: 2004-10-19
forum: General Help
---

### Post by paul.hendrick on 2004-10-19
Hi all,
I've built wxWidgets to use GTK2, and now i'm trying to get audacity to  build so it uses gtk2, and not 1. when i compile audacity though, the build fails with the below output. does anyone have any ideas why?

thanks for any help!
paul

```

D_FILE_OFFSET_BITS=64 -D_LARGE_FILES   BlockFile.cpp -o obj/BlockFile.o
BlockFile.cpp&#58; In constructor `AliasBlockFile&#58;&#58;AliasBlockFile&#40;wxFileName,
   wxFileName, int, int, int&#41;'&#58;
BlockFile.cpp&#58;466&#58; error&#58; ambiguous overload for 'operator+' in '
   wxFileName&#58;&#58;GetFullPath&#40;wxPathFormat&#41; const&#40;wxPATH_NATIVE&#41; + &quot;.auf&quot;'
/usr/include/wx/string.h&#58;1241&#58; error&#58; candidates are&#58; wxString operator+&#40;const
   wxString&amp;, const wxString&amp;&#41; &lt;near match&gt;
/usr/include/wx/string.h&#58;1242&#58; error&#58;                 wxString operator+&#40;const
   wxString&amp;, wchar_t&#41; &lt;near match&gt;
/usr/include/wx/string.h&#58;1243&#58; error&#58;                 wxString
   operator+&#40;wchar_t, const wxString&amp;&#41; &lt;near match&gt;
/usr/include/wx/string.h&#58;1245&#58; error&#58;                 wxString operator+&#40;const
   wxChar*, const wxString&amp;&#41; &lt;near match&gt;
/usr/include/wx/string.h&#58;1248&#58; error&#58;                 wxString operator+&#40;const
   wxString&amp;, const wxWCharBuffer&amp;&#41; &lt;near match&gt;
/usr/include/wx/longlong.h&#58;921&#58; error&#58;                 wxLongLong
   operator+&#40;long int, const wxLongLong&amp;&#41; &lt;near match&gt;
/usr/include/wx/longlong.h&#58;934&#58; error&#58;                 wxULongLong
   operator+&#40;long unsigned int, const wxULongLong&amp;&#41; &lt;near match&gt;
make&#91;1&#93;&#58; *** &#91;obj/BlockFile.o&#93; Error 1
make&#91;1&#93;&#58; Leaving directory `/opt/audacity-src-1.2.2/src'
make&#58; *** &#91;audacity&#93; Error 2
```

---

