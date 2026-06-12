---
title: "Helvetica remapped in Chrome and Epiphany-webkit"
date: 2009-12-18
forum: General Help
---

### Post by asrai on 2009-12-18
I have bought a number of fonts (including Helvetica) and have them installed. I am running Karmic 9.10 64bit.

When a website prescribes Helvetica in the css, in firefox, I see Helvetica.:guitar:

In Chrome, I get Arial.

In Epiphany I get Deja Vu Sans.

I'd really like to use Chrome as my default browser. Or Epiphany would be fine too. But the font issue is a problem.

To say it is driving me mad is perhaps an understatement. I know it doesn't sound like a big deal but is an itch I can't scratch!

fc-match -v "Helvetica" results in:

Pattern has 32 elts (size 48)
	family: "DejaVu Sans"(s)
	familylang: "en"(s)
	style: "Book"(s)
	stylelang: "en"(s)
	fullname: "DejaVu Sans"(s)
	fullnamelang: "en"(s)
	slant: 0(i)(s)
	weight: 80(i)(s)
	width: 100(i)(s)
	size: 12(f)(s)
	pixelsize: 12.5(f)(s)
	foundry: "unknown"(s)
	antialias: FcTrue(w)
	hintstyle: 1(i)(w)
	hinting: FcTrue(w)
	verticallayout: FcFalse(s)
	autohint: FcFalse(s)
	globaladvance: FcTrue(s)
	file: "/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf"(s)
	index: 0(i)(s)
	outline: FcTrue(s)
	scalable: FcTrue(s)
	dpi: 75(f)(s)
	scale: 1(f)(s)
	charset: 0000: 00000000 ffffffff ffffffff 7fffffff 00000000 ffffffff ffffffff ffffffff
	0001: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
	0002: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 008873ff
	0003: ffffffff ffffffff f58effff 7cff0007 ffffd7f0 fffffffb ffffffff ffffffff
	0004: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
	0005: 3fffffff fffe003f fe7fffff fffffffe 000006ff ffff0000 ffff00cf 001f07ff
	0006: 882016c0 07fffffe 043fffff fe10ffff 012600ff 84208252 00205040 03ff0000
	0007: 00000000 00000000 00000000 00000000 00000000 00000000 ffffffff 073ff8ff
	000e: 00000000 80000000 00000000 00000000 fef02596 3bffecae 33ff3f5f 00000000
	0010: 00000000 00000000 00000000 00000000 00000000 ffffffff ffff003f 1fffffff
	0014: effffefe ffbfffff fff7f7ff ffffffff ffffffff 3fffffff ffffffff fffff7ff
	0015: ffff00ff 7fffffff fffdffff fff007ff 007ffc3f 0000ffff 40000000 00000002
	0016: 00000000 00000000 000000c0 007fc000 1fffffff 00000000 00000000 00000000
	001d: ffdfffff ffff7fcf efffffff 098007ff f8000020 ffffffff 000003f0 00000000
	001e: ffffffff ffffffff ffffffff ffffffff cfffffff ffffffff ffffffff 03ffffff
	001f: 3f3fffff ffffffff aaff3f3f 3fffffff ffffffff ffdfffff efcfffdf 7fdcffff
	0020: ffffffff fffffcff ffffffff fff3fc0f 001f7fff 003fffff 18c30000 00000002
	0021: fffffbff ffffffff fff84bff ffffffff ffff001f ffffffff ffffffff ffffffff
	0022: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
	0023: f303ffff 000019f3 00000000 24380000 f8100080 00007fff 0000c000 00000028
	0024: 00000000 0000000c 00000000 000003ff 00000000 00000000 00000000 00000000
	0025: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
	0026: ffffffff ffffffff ffffffff ffffffff 1fffffff 01ffffff 00000000 00000000
	0027: fffff3de fffffeff 7f47afff fffffffe ff1fffff 7ffeffff 00000060 ffff0fc1
	0028: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
	0029: 00000cc0 00000000 00000003 00000000 00000018 00000000 003fc000 0c000800
	002a: 1ffff007 00008000 00000000 e0000000 ffffffff 07ffc001 00000000 06000000
	002b: 87ffffff 0000001f 00180000 00000000 00000000 00000000 00000000 00000000
	002c: 00000000 00000000 00000000 3efeffff 00000000 00000000 00000000 00000000
	002d: 00000000 ffff0000 ffffffff 0000803f 00000000 00000000 00000000 00000000
	002e: 01000000 0000403c 00000000 00000000 00000000 00000000 00000000 00000000
	004d: 00000000 00000000 00000000 00000000 00000000 00000000 ffffffff ffffffff
	00a6: 00000000 00000000 00f330f0 00007ffc 00303c00 00000000 00000000 00000000
	00a7: f87fff00 ffff0fc0 0000cfc0 00000000 00001e0f 00000000 00000000 f8000000
	00f0: 00000003 00000000 00000000 00000000 00000000 00000000 00000000 00000000
	00f6: 00000000 00000000 00000000 00000000 00000000 00000000 00000020 00000000
	00fb: e0f8007f 5f7fffff fffcffdb ffffffff c03ffc03 00000000 06000000 f0000300
	00fe: 00000000 0000000f 00000000 ffdf0000 ffffffff ffffffff ffffffff 9fffffff
	00ff: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 2e000000
	01d3: ffffffff ffffffff 007fffff 00000000 00000000 00000000 00000000 00000000
	01d5: 00000000 7b000000 fffdfc5f 00000fff 00000000 ffffffff 000fffff 00000000
	01d7: 00000000 00000000 00000000 00000000 00000000 00000000 ff000000 00000fff
(s)
	lang: aa|ab|af|ar|ast|ava|ay|az|az-ir|ba|bam|be|bg|bi|bin|br|bs|bua|ca|ce|ch|chm|co|cs|cu|cv|cy|da|de|el|en|eo|es|et|eu|fa|fi|fj|fo|fr|ful|fur|fy|ga|gd|gl|gn|gv|ha|haw|he|ho|hr|hu|hy|ia|ibo|id|ie|ik|io|is|it|iu|ka|kaa|ki|kk|kl|ku|ku-ir|kum|kv|kw|ky|la|lb|lez|ln|lo|lt|lv|mg|mh|mi|mk|mo|mt|nb|nds|nl|nn|no|nr|nso|ny|oc|om|os|pl|pt|rm|ro|ru|sah|sco|se|sel|sh|shs|sk|sl|sm|sma|smj|smn|sms|so|sq|sr|ss|st|sv|sw|tg|tk|tn|to|tr|ts|tt|tw|tyv|ug|uk|uz|ven|vi|vo|vot|wa|wen|wo|xh|yap|yi|yo|zu(s)
	fontversion: 150077(i)(s)
	capability: "otlayout:DFLT otlayout:arab otlayout:armn otlayout:brai otlayout:cans otlayout:cher otlayout:cyrl otlayout:geor otlayout:grek otlayout:hani otlayout:hebr otlayout:kana otlayout:lao  otlayout:latn otlayout:math otlayout:nko  otlayout:ogam otlayout:runr otlayout:tfng otlayout:thai"(s)
	fontformat: "TrueType"(s)
	embeddedbitmap: FcTrue(s)
	decorative: FcFalse(s)
	lcdfilter: 1(i)(w)

I removed every association I could find in /etc/fonts/conf.d/30-metric-aliases.conf 

Please help put me out of my misery. I'll be forever grateful and indebted to you! :popcorn:

---

