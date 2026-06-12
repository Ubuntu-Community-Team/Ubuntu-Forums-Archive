---
title: "Ubuntu Firefox Modifications 0.9rc2 breaks ask.com search"
date: 2010-10-06
forum: General Help
---

### Post by mindkeep on 2010-10-06
The latest version is mucking with search results from at least the ask.com and google.com results when queried from the search toolbar.

I've always been wary of it. I'm pretty sure it was disabled previous to today's update. I wouldn't have noticed if every result hadn't redirected to the same search page (ie. someone broke something). Seems pretty shady.

Disabling the Add-on, restores proper search behavior. Enabling the Add-on borks things again.

It's broken, fine, I'm sure it will be fixed, but my question is this: What is the Add-on actually doing? This feels very shady Ubuntu.

---

### Post by lovinglinux on 2010-10-06
[http://packages.ubuntu.com/lucid/ubufox](http://packages.ubuntu.com/lucid/ubufox)

> Extension package for Firefox provides ubuntu specific configuration defaults as well as apt support for firefox plugins/extensions. 

The extension provides custom search engines, the default Ubuntu home page, apturl support and other stuff.

---

### Post by mindkeep on 2010-10-07
Thanks for the quick response.
> **lovinglinux said:**
> and other stuff.
What is other stuff? Why would it need to modify the search url? This begs the question, what else is it reading? recording? O_o If it were just "helping" by making things like flash install easier, fine, but that's obviously not the case.

---

### Post by mindkeep on 2010-10-07
Poking a little further, /usr/share/xul-ext/ubufox/searchplugins/ask.xml looks like it adds

  <Param name="o" value="1576"/>
  <Param name="l" value="dis"/>

to the search params specifically for ask.com. so

[http://www.ask.com/web?q=0.9rc2](http://www.ask.com/web?q=0.9rc2)
gets changed to
[http://www.ask.com/web?q=0.9rc2&o=1576&l=dis](http://www.ask.com/web?q=0.9rc2&o=1576&l=dis)

in the resulting page, all search result links point to "http://www.ask.com/web?q=0.9rc2&o=1576&l=dis" vs whatever they should be linking to. Again, what are the additional fields supposed to buy us?

I don't have enough time to dig through the javascript at the moment. It looks like the results are broken by ask.com (since the plugin is currently disabled). I apologize if my tone has been harsh, but on the surface this reeks of virus like behavior.

---

### Post by lovinglinux on 2010-10-07
> **mindkeep said:**
> Thanks for the quick response.

What is other stuff? Why would it need to modify the search url? This begs the question, what else is it reading? recording? O_o If it were just "helping" by making things like flash install easier, fine, but that's obviously not the case.

> **mindkeep said:**
> Poking a little further, /usr/share/xul-ext/ubufox/searchplugins/ask.xml looks like it adds

  <Param name="o" value="1576"/>
  <Param name="l" value="dis"/>

to the search params specifically for ask.com. so

[http://www.ask.com/web?q=0.9rc2](http://www.ask.com/web?q=0.9rc2)
gets changed to
[http://www.ask.com/web?q=0.9rc2&o=1576&l=dis](http://www.ask.com/web?q=0.9rc2&o=1576&l=dis)

in the resulting page, all search result links point to "http://www.ask.com/web?q=0.9rc2&o=1576&l=dis" vs whatever they should be linking to. Again, what are the additional fields supposed to buy us?

I don't have enough time to dig through the javascript at the moment. It looks like the results are broken by ask.com (since the plugin is currently disabled). I apologize if my tone has been harsh, but on the surface this reeks of virus like behavior.

If you don't trust Ubufox, why would you trust Ubuntu at all? You still can disable the extension anyway.

Ubuntu is free, but Canonical needs to make money somehow, so it makes partnerships with search engines. That's probably why it modifies the search string.

---

