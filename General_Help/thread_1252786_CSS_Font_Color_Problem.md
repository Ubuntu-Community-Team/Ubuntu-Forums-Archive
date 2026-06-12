---
title: "CSS Font Color Problem"
date: 2009-08-29
forum: General Help
---

### Post by vhenry on 2009-08-29
Hope this is the right place for this question. I'm having a problem on a seemingly elementary issue, can't change the font color of the nav bar on my [site]("http://www.veronicawrites.com"). Even changing in firebug for a preview doesn't work. Any ideas? Here is the css:
```

#container {

	font-family: Verdana, Arial, Helvetica, sans-serif;

	width: 780px;

	margin-right: auto;

	margin-left: auto;
	background: #F9DFB3;

#top {
	font-size: medium;
}

.navtext {
	color: #FFFFCC;
}
```

Header.php
```

<div id="top" class="navtext">
<div><img src="images/vwbanner.gif" alt="veronica writes banner" width="780" height="150"/></div>  
	<table width="100%" border="0" cellpadding="0" cellspacing="0" background="images/vwnav.gif">

                <tr>

                    <td width="20%">

                        <a href="index.php" target="_self" class="style13">Home</a>

                    </td>

                    <td width="20%">

                        <a href="about me.php" target="_self" class="style13">About Me</a>

                    </td>

                    <td width="20%">

                        <a href="credits.php" target="_self" class="style13">Credits</a>

                    </td>

                    <td width="20%">

                        <a href="fiction.php" target="_self" class="style13">Fiction</a>

                    </td>

                    <td width="20%">

                        <a href="contact.php" target="_self" class="style13">Contact</a>

                    </td>

                 </tr>
    </table>
</div>

```

---

### Post by vhenry on 2009-08-29
problem solved - needed to change the global link setting.

---

