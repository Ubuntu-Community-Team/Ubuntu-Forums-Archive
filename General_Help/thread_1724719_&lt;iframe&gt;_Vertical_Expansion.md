---
title: "&lt;iframe&gt; Vertical Expansion"
date: 2011-04-08
forum: General Help
---

### Post by gerowen on 2011-04-08
I have a web page that consists of an inline frame.  I have it this way just so I can keep a links bar from another page of mine on top of it.  I want to remove the inline frame's scrollbars and have it automatically adjust its vertical size to fit the page currently loaded.  Here's the code to the page in question.  Basically I want to avoid having two sets of scrollbars when the only thing on the page is the <iframe>.

```

<html>
<head>
<meta content="text/html; charset=ISO-8859-1"
http-equiv="Content-Type">
<title>Family Tree</title>
</head>
<body>
<table style="text-align: left; width: 100%;" border="1" cellpadding="2"
cellspacing="2">
<tbody>
<tr>
<td style="vertical-align: top; text-align: center; height: 30px;"><a
href="index.html"><img alt="Image linked back to home page."
title="Back to homepage" src="images/homebutton.png"
style="border: 0px solid ; width: 69px; height: 23px;"></a><a
href="family_tree/index.html"><img alt="Family Tree Link Button"
title="Family Tree" src="images/familytreebutton.png"
style="border: 0px solid ; width: 112px; height: 23px;"></a><a
href="ftp://adams-family.homeip.net/"><img alt="FTP Link Button"
title="Log into your FTP Folder" src="images/ftpbutton.png"
style="border: 0px solid ; width: 98px; height: 23px;"></a><a
href="software.html"><img alt="Software linked button"
title="Software Page" src="images/softwarebutton.png"
style="border: 0px solid ; width: 93px; height: 23px;"></a></td>
</tr>
</tbody>
</table>
<iframe id="frame" src="family_tree/index.html" height="100%"
width="100%"></iframe>
</body>
</html>

```

---

