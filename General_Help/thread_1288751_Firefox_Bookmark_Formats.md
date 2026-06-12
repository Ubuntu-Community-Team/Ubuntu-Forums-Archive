---
title: "Firefox Bookmark Formats"
date: 2009-10-11
forum: General Help
---

### Post by Rytron on 2009-10-11
Hi.
I notice that Firefox bookmarks can be backed up to .html & .json formats. I always opt for html. What is the difference in choosing json? Is there an advantage? I have noticed that backing up in json takes approximately ½ the size.

---

### Post by antony.s on 2009-10-11
JSON is the new format that firefox3 uses to store bookmarks, more details about why are here: [http://www.lytebyte.com/2008/06/19/understanding-how-and-where-firefox-3-bookmarks-are-saved/](http://www.lytebyte.com/2008/06/19/understanding-how-and-where-firefox-3-bookmarks-are-saved/)

HTML was the old format firefox2 used

The format you choose to backup/export to depends on what you want to use them for and both options are available for backwards compatibility (and making it easier to import to other browsers that can't read json)

---

### Post by lovinglinux on 2009-10-11
With json you can restore a backup, completely replacing your current bookmarks, while with html you can only import, merging everything, which usually means duplicated folders and bookmarks.

This is the HTML format:

```
        <DT><A HREF="http://ubuntuforums.org/showthread.php?t=765421" ADD_DATE="1238671157" LAST_MODIFIED="1250405056" ICON_URI="http://ubuntuforums.org/favicon.ico" ICON="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1gUYBy8UWHdfBwAAAcJJREFUOMuVk09IVFEUxn/nNb7pkbV7r4jQQHKTbQya2rSxJJmoRbYLEqZl0MJolataFkW4k0ebmDaVCD4EEQdsEW+aTRuxdKGDCDMuhJjxNWN5WnjHzHkqntW958/lu993PjhEhHjDId5iiHerkZO9mjXjtADdwGVgY+lLcqo0a3835ekU5R6ARNNg7uxRqmsOo/UscKORb79Se1SatceBa0A2FoEqwoQ7jeocn6ojwFfAMuUa8LRWkYVkqy6LHxWaHwjcAeAt8AfdvMDoegewCnjAfeCOaS0C58WPKvIPutvKOvPAKYQVNqRbbpdLu3gZAR6Y65D40XNLM067ZpxBwnonEJm/PN49bOIZUDfn3gaJH4GLzNe/0dXyBpFXbOpMnDLiR0XNOPeADuBXrAoHRd4/vuMWkTDE9HPOziHyAQBLrgLvYxapDXgH2MBn4LUlfrQkfvSSlP0DcLawygsd807GABgywwCTB8qYv3lkXxlTlCt7LlI+bcUuUuKELvz+KcspyoUmEkVQzR3ro7rmQDK7YxjgyaVAr29JqQ9JU9jXTCHef2Y6M6BTp++ybSZJr/YcVkE0cIc1cBc1cLft/BckXKkAO9v5fAAAAABJRU5ErkJggg==" LAST_CHARSET="ISO-8859-1">Ubuntu Security - Ubuntu Forums</A>
<DD> Ubuntu Security Security Discussions
```

This is the json format:

```
"type":"text/x-moz-place-container","root":"bookmarksMenuFolder","children":[{"title":"archive","id":6,"parent":2,"dateAdded":1238671114404468,"lastModified":1254513564257843,"annos":[{"name":"bookmarkPropertiesDialog/folderLastUsed","flags":0,"expires":4,"mimeType":null,"type":2,"value":1254513563882},{"name":"placesInternal/GUID","flags":0,"expires":4,"mimeType":null,"type":3,"value":"fyfetrca-2"}],"type":"text/x-moz-place-container","children":[{"title":"Ubuntu Security - Ubuntu Forums","id":7,"parent":6,"dateAdded":1238671157132310,"lastModified":1250405056492407,"annos":[{"name":"bookmarkProperties/description","flags":0,"expires":4,"mimeType":null,"type":3,"value":" Ubuntu Security Security Discussions"},{"name":"placesInternal/GUID","flags":0,"expires":4,"mimeType":null,"type":3,"value":"fyfetrca-p"}],"type":"text/x-moz-place","uri":"http://ubuntuforums.org/showthread.php?t=765421","charset":"ISO-8859-1"}
```

---

### Post by Rytron on 2009-10-11
Wow, that was a rapid response! Thank you antony.s & lovinglinux.

That was a great point about html bookmarks merging as opposed to json overwriting. json seems to have the edge.

---

