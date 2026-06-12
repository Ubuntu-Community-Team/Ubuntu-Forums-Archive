---
title: "dvd menu buttons"
date: 2006-04-13
forum: General Help
---

### Post by pumaman_scotland on 2006-04-13
Hi,

when I make a menu, it looks fine on my widescreen TV but messes up on my 4:3 TV. It seams that the buttons aren't scaled when the image is letterboxed.

To illustrate, this is what a menu might look like in widescreen:
[IMG]http://www.pumaman.me.uk/misc/widescreen.png[/IMG]
and this is what the same menu would look like letterboxed on a standard TV.: 
[IMG]http://www.pumaman.me.uk/misc/letterbox.png[/IMG]

Does anyone have the same problem, and can anyone help?

My spumux xml looks like this:
```
<subpictures>
  <stream>
    <spu start="00:00:00.0" end="00:00:00.0"
         image="buttons.png"
         highlight="buttonsh.png"
         select="buttonsh.png"
         force="yes"
         autooutline="infer"
         autoorder="rows"/>
  </stream>
</subpictures>

```

and my dvdauthor xml looks like this:
```
	<menus>
		<video aspect="16:9" widescreen="nopanscan" />
		<pgc>
			<vob file="menu.mpg" pause="0" />
			<button>{jump title 1;}</button>
			<button>{jump title 2;}</button>
			<post>jump cell 1;</post>
		</pgc>
	</menus>

```

thanks
David

---

