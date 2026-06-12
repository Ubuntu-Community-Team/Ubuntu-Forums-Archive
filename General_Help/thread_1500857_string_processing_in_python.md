---
title: "string processing in python"
date: 2010-06-03
forum: General Help
---

### Post by konjeng on 2010-06-03
<meta name="keywords" content="search, searches, search engine,  directory, directories, category, categories, help, multi media, maps,  business finder, yellow pages, white pages,  people search, find people,  searching, searchers, advanced search, search help, search guide,  search tips, search tools"> 
here i am trying to extract the data within double quotations but it's not working. please help!!!!
#!/usr/bin/python

fid=open("in.altavista.com.html","r")
buff=fid.read() 
buff=buff.lower()

st=buff.find('content="',0)
while st!=-1:
    en=buff.find('">',st) 
    url=buff[st:en]
    print url
    st=buff.find('content="',en)



thanks in advance

---

