---
title: "Unable to install libre-office or open office"
date: 2012-02-20
forum: General Help
---

### Post by nutmegy on 2012-02-20
Hi guys

I'm new to the world of Ubuntu but enjoying the ride so far... 

I was mucking about with installing Open Office and now decided to uninstall it... but i cant!! i keep on getting the follwing

```
nutmeg@nutmeg:~$ sudo apt-get purge "openoffice*.*"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openoffice.org-updatedicts' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hunspell' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-core' for regex 'openoffice*.*'
Note, selecting 'openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-at' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-gl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-uz' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-writer' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-af' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-impress' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-hr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ro' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sh' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-zu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ui' for regex 'openoffice*.*'
Note, selecting 'libbase-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libflute-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libfonts-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libloader-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libformula-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-base' for regex 'openoffice*.*'
Note, selecting 'liblayout-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'librepository-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libxml-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libpentaho-reporting-flow-engine-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'libserializer-java-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-common' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dev-doc' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-kde' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eo' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-et' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-et' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fo' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-lv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-lv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ss' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-st' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ve' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-xh' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-zu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-en-au' for regex 'openoffice*.*'
Note, selecting 'openoffice.org2-thesaurus' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ne' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ro' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-sk' for regex 'openoffice*.*'
Note, selecting 'docvert-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dmaths' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-mysql-connector' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-presentation-minimizer' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-presenter-console' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-report-builder' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-sdbc-postgresql' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-voikko' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-wiki-publisher' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-da' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-dz' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-el' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-en-gb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-et' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-eu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-gl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-hi-in' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-ja' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-km' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-ko' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-nl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-om' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-pt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-pt-br' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-sl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-sv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-zh-cn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-help-zh-tw' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-da' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-el' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ga' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-id' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-is' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-nl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-pt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-uk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-lt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-af' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ar' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-as' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ast' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-be-by' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-bg' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-bn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-br' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-bs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-cy' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-da' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-dz' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-el' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-en-gb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-en-za' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-eo' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-et' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-eu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-fa' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ga' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-gl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-gu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-he' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-hi-in' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-hr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-id' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-in' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ja' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ka' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-km' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ko' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ku' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-lt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-lv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-mk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ml' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-mn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-mr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-nb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ne' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-nl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-nn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-nr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ns' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-oc' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-om' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-or' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-pa-in' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-pt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-pt-br' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ro' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-rw' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-si' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-sk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-sl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-sr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ss' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-st' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-sv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ta' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-te' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-tg' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-th' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-tn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-tr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ts' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ug' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-uk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-uz' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-ve' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-vi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-xh' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-za' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-zh-cn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-zh-tw' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-l10n-zu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org2-thesaurus-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-calc' for regex 'openoffice*.*'
Note, selecting 'libopenoffice-oodoc-perl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-draw' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-java-common' for regex 'openoffice*.*'
Note, selecting 'kde-thumbnailer-openoffice' for regex 'openoffice*.*'
Note, selecting 'libming-fonts-openoffice' for regex 'openoffice*.*'
Note, selecting 'mozilla-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ns' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tl' for regex 'openoffice*.*'
Note, selecting 'openclipart-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dtd-officedocument1.0' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-emailmerge' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-filter-binfilter' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-filter-mobiledev' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-gnome' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-gtk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-math' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-officebean' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-ogltrans' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-pdfimport' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-starter-guide' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-andromeda' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-crystal' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-galaxy' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-hicontrast' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-oxygen' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-style-tango' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-writer2latex' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-writer2xhtml' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-zemberek' for regex 'openoffice*.*'
Note, selecting 'python-openoffice' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-ure' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-en-gb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-calc' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-math' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-base' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-draw' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-debian-menus' for regex 'openoffice*.*'
Note, selecting 'openofficeorg-desktop-integration' for regex 'openoffice*.*'
Note, selecting 'openofficeorg-debian-menus' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-bundled' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-desktop-integration' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-unbundled' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-en' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-writer' for regex 'openoffice*.*'
Note, selecting 'openoffice.org3-impress' for regex 'openoffice*.*'
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Note, selecting 'hunspell-eu-es' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-zu' instead of 'openoffice.org-hyphenation-ui'
Note, selecting 'myspell-ca' instead of 'openoffice.org-spellcheck-ca'
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-et' instead of 'openoffice.org-hyphenation-et'
Note, selecting 'myspell-et' instead of 'openoffice.org-spellcheck-et'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-lv' instead of 'openoffice.org-hyphenation-lv'
Note, selecting 'myspell-lv' instead of 'openoffice.org-spellcheck-lv'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ru' instead of 'openoffice.org-spellcheck-ru'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-cs'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-da'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-el'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-es'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-is'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-nl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-pt'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ru'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sk'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sv'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-uk'
Note, selecting 'openoffice.org-thesaurus-it' instead of 'openoffice.org2-thesaurus-it'
Note, selecting 'ming-fonts-opensymbol' instead of 'libming-fonts-openoffice'
Note, selecting 'myspell-fi' instead of 'openoffice.org-spellcheck-fi'
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Note, selecting 'openoffice.org-debian-menus' instead of 'openoffice.org-desktop-integration'
Note, selecting 'openoffice.org-debian-menus' instead of 'openoffice.org-unbundled'
Package hunspell-eu-es is not installed, so not removed
Package hunspell-gl-es is not installed, so not removed
Package hunspell-uz is not installed, so not removed
Package hyphen-pl is not installed, so not removed
Package hyphen-zu is not installed, so not removed
Package libbase-java-openoffice.org is not installed, so not removed
Package libflute-java-openoffice.org is not installed, so not removed
Package libfonts-java-openoffice.org is not installed, so not removed
Package libformula-java-openoffice.org is not installed, so not removed
Package liblayout-java-openoffice.org is not installed, so not removed
Package libloader-java-openoffice.org is not installed, so not removed
Package libpentaho-reporting-flow-engine-java-openoffice.org is not installed, so not removed
Package librepository-java-openoffice.org is not installed, so not removed
Package libserializer-java-openoffice.org is not installed, so not removed
Package libxml-java-openoffice.org is not installed, so not removed
Package myspell-ca is not installed, so not removed
Package myspell-eo is not installed, so not removed
Package myspell-es is not installed, so not removed
Package myspell-et is not installed, so not removed
Package myspell-fo is not installed, so not removed
Package myspell-lv is not installed, so not removed
Package myspell-nb is not installed, so not removed
Package myspell-nn is not installed, so not removed
Package myspell-nr is not installed, so not removed
Package myspell-ru is not installed, so not removed
Package myspell-ss is not installed, so not removed
Package myspell-st is not installed, so not removed
Package myspell-tn is not installed, so not removed
Package myspell-ve is not installed, so not removed
Package myspell-xh is not installed, so not removed
Package myspell-zu is not installed, so not removed
Package mythes-pl is not installed, so not removed
Package openoffice.org is not installed, so not removed
Package openoffice.org-base is not installed, so not removed
Package openoffice.org-common is not installed, so not removed
Package openoffice.org-help-ca is not installed, so not removed
Package openoffice.org-help-cs is not installed, so not removed
Package openoffice.org-help-da is not installed, so not removed
Package openoffice.org-help-de is not installed, so not removed
Package openoffice.org-help-dz is not installed, so not removed
Package openoffice.org-help-el is not installed, so not removed
Package openoffice.org-help-en-gb is not installed, so not removed
Package openoffice.org-help-en-us is not installed, so not removed
Package openoffice.org-help-es is not installed, so not removed
Package openoffice.org-help-et is not installed, so not removed
Package openoffice.org-help-eu is not installed, so not removed
Package openoffice.org-help-fi is not installed, so not removed
Package openoffice.org-help-fr is not installed, so not removed
Package openoffice.org-help-gl is not installed, so not removed
Package openoffice.org-help-hi-in is not installed, so not removed
Package openoffice.org-help-hu is not installed, so not removed
Package openoffice.org-help-it is not installed, so not removed
Package openoffice.org-help-ja is not installed, so not removed
Package openoffice.org-help-km is not installed, so not removed
Package openoffice.org-help-ko is not installed, so not removed
Package openoffice.org-help-nl is not installed, so not removed
Package openoffice.org-help-om is not installed, so not removed
Package openoffice.org-help-pl is not installed, so not removed
Package openoffice.org-help-pt is not installed, so not removed
Package openoffice.org-help-pt-br is not installed, so not removed
Package openoffice.org-help-ru is not installed, so not removed
Package openoffice.org-help-sl is not installed, so not removed
Package openoffice.org-help-sv is not installed, so not removed
Package openoffice.org-help-zh-cn is not installed, so not removed
Package openoffice.org-help-zh-tw is not installed, so not removed
Package openoffice.org-hyphenation-af is not installed, so not removed
Package openoffice.org-hyphenation-ca is not installed, so not removed
Package openoffice.org-hyphenation-de is not installed, so not removed
Package openoffice.org-hyphenation-en-us is not installed, so not removed
Package openoffice.org-hyphenation-fr is not installed, so not removed
Package openoffice.org-hyphenation-hr is not installed, so not removed
Package openoffice.org-hyphenation-hu is not installed, so not removed
Package openoffice.org-hyphenation-it is not installed, so not removed
Package openoffice.org-hyphenation-lt is not installed, so not removed
Package openoffice.org-hyphenation-ro is not installed, so not removed
Package openoffice.org-hyphenation-sh is not installed, so not removed
Package openoffice.org-hyphenation-sl is not installed, so not removed
Package openoffice.org-hyphenation-sr is not installed, so not removed
Package openoffice.org-hyphenation-zu is not installed, so not removed
Package openoffice.org-l10n-af is not installed, so not removed
Package openoffice.org-l10n-ar is not installed, so not removed
Package openoffice.org-l10n-as is not installed, so not removed
Package openoffice.org-l10n-ast is not installed, so not removed
Package openoffice.org-l10n-be-by is not installed, so not removed
Package openoffice.org-l10n-bg is not installed, so not removed
Package openoffice.org-l10n-bn is not installed, so not removed
Package openoffice.org-l10n-br is not installed, so not removed
Package openoffice.org-l10n-bs is not installed, so not removed
Package openoffice.org-l10n-ca is not installed, so not removed
Package openoffice.org-l10n-cs is not installed, so not removed
Package openoffice.org-l10n-cy is not installed, so not removed
Package openoffice.org-l10n-da is not installed, so not removed
Package openoffice.org-l10n-de is not installed, so not removed
Package openoffice.org-l10n-dz is not installed, so not removed
Package openoffice.org-l10n-el is not installed, so not removed
Package openoffice.org-l10n-en-gb is not installed, so not removed
Package openoffice.org-l10n-en-za is not installed, so not removed
Package openoffice.org-l10n-eo is not installed, so not removed
Package openoffice.org-l10n-es is not installed, so not removed
Package openoffice.org-l10n-et is not installed, so not removed
Package openoffice.org-l10n-eu is not installed, so not removed
Package openoffice.org-l10n-fa is not installed, so not removed
Package openoffice.org-l10n-fi is not installed, so not removed
Package openoffice.org-l10n-fr is not installed, so not removed
Package openoffice.org-l10n-ga is not installed, so not removed
Package openoffice.org-l10n-gl is not installed, so not removed
Package openoffice.org-l10n-gu is not installed, so not removed
Package openoffice.org-l10n-he is not installed, so not removed
Package openoffice.org-l10n-hi-in is not installed, so not removed
Package openoffice.org-l10n-hr is not installed, so not removed
Package openoffice.org-l10n-hu is not installed, so not removed
Package openoffice.org-l10n-id is not installed, so not removed
Package openoffice.org-l10n-in is not installed, so not removed
Package openoffice.org-l10n-it is not installed, so not removed
Package openoffice.org-l10n-ja is not installed, so not removed
Package openoffice.org-l10n-ka is not installed, so not removed
Package openoffice.org-l10n-km is not installed, so not removed
Package openoffice.org-l10n-ko is not installed, so not removed
Package openoffice.org-l10n-ku is not installed, so not removed
Package openoffice.org-l10n-lt is not installed, so not removed
Package openoffice.org-l10n-lv is not installed, so not removed
Package openoffice.org-l10n-mk is not installed, so not removed
Package openoffice.org-l10n-ml is not installed, so not removed
Package openoffice.org-l10n-mn is not installed, so not removed
Package openoffice.org-l10n-mr is not installed, so not removed
Package openoffice.org-l10n-nb is not installed, so not removed
Package openoffice.org-l10n-ne is not installed, so not removed
Package openoffice.org-l10n-nl is not installed, so not removed
Package openoffice.org-l10n-nn is not installed, so not removed
Package openoffice.org-l10n-nr is not installed, so not removed
Package openoffice.org-l10n-ns is not installed, so not removed
Package openoffice.org-l10n-oc is not installed, so not removed
Package openoffice.org-l10n-om is not installed, so not removed
Package openoffice.org-l10n-or is not installed, so not removed
Package openoffice.org-l10n-pa-in is not installed, so not removed
Package openoffice.org-l10n-pl is not installed, so not removed
Package openoffice.org-l10n-pt is not installed, so not removed
Package openoffice.org-l10n-pt-br is not installed, so not removed
Package openoffice.org-l10n-ro is not installed, so not removed
Package openoffice.org-l10n-ru is not installed, so not removed
Package openoffice.org-l10n-rw is not installed, so not removed
Package openoffice.org-l10n-si is not installed, so not removed
Package openoffice.org-l10n-sk is not installed, so not removed
Package openoffice.org-l10n-sl is not installed, so not removed
Package openoffice.org-l10n-sr is not installed, so not removed
Package openoffice.org-l10n-ss is not installed, so not removed
Package openoffice.org-l10n-st is not installed, so not removed
Package openoffice.org-l10n-sv is not installed, so not removed
Package openoffice.org-l10n-ta is not installed, so not removed
Package openoffice.org-l10n-te is not installed, so not removed
Package openoffice.org-l10n-tg is not installed, so not removed
Package openoffice.org-l10n-th is not installed, so not removed
Package openoffice.org-l10n-tn is not installed, so not removed
Package openoffice.org-l10n-tr is not installed, so not removed
Package openoffice.org-l10n-ts is not installed, so not removed
Package openoffice.org-l10n-ug is not installed, so not removed
Package openoffice.org-l10n-uk is not installed, so not removed
Package openoffice.org-l10n-uz is not installed, so not removed
Package openoffice.org-l10n-ve is not installed, so not removed
Package openoffice.org-l10n-vi is not installed, so not removed
Package openoffice.org-l10n-xh is not installed, so not removed
Package openoffice.org-l10n-za is not installed, so not removed
Package openoffice.org-l10n-zh-cn is not installed, so not removed
Package openoffice.org-l10n-zh-tw is not installed, so not removed
Package openoffice.org-l10n-zu is not installed, so not removed
Package openoffice.org-thesaurus-ca is not installed, so not removed
Package openoffice.org-thesaurus-cs is not installed, so not removed
Package openoffice.org-thesaurus-de is not installed, so not removed
Package openoffice.org-thesaurus-de-ch is not installed, so not removed
Package openoffice.org-thesaurus-en-au is not installed, so not removed
Package openoffice.org-thesaurus-en-us is not installed, so not removed
Package openoffice.org-thesaurus-fr is not installed, so not removed
Package openoffice.org-thesaurus-hu is not installed, so not removed
Package openoffice.org-thesaurus-it is not installed, so not removed
Package openoffice.org-thesaurus-ne is not installed, so not removed
Package openoffice.org-thesaurus-ro is not installed, so not removed
Package openoffice.org-thesaurus-ru is not installed, so not removed
Package openoffice.org-thesaurus-sk is not installed, so not removed
Package openoffice.org-voikko is not installed, so not removed
Package docvert-openoffice.org is not installed, so not removed
Package kde-thumbnailer-openoffice is not installed, so not removed
Package libopenoffice-oodoc-perl is not installed, so not removed
Package ming-fonts-opensymbol is not installed, so not removed
Package mozilla-openoffice.org is not installed, so not removed
Package myspell-fi is not installed, so not removed
Package myspell-fr-gut is not installed, so not removed
Package myspell-ns is not installed, so not removed
Package myspell-tl is not installed, so not removed
Package openoffice.org-calc is not installed, so not removed
Package openoffice.org-dmaths is not installed, so not removed
Package openoffice.org-draw is not installed, so not removed
Package openoffice.org-emailmerge is not installed, so not removed
Package openoffice.org-filter-binfilter is not installed, so not removed
Package openoffice.org-filter-mobiledev is not installed, so not removed
Package openoffice.org-gnome is not installed, so not removed
Package openoffice.org-gtk is not installed, so not removed
Package openoffice.org-impress is not installed, so not removed
Package openoffice.org-java-common is not installed, so not removed
Package openoffice.org-kde is not installed, so not removed
Package openoffice.org-math is not installed, so not removed
Package openoffice.org-mysql-connector is not installed, so not removed
Package openoffice.org-officebean is not installed, so not removed
Package openoffice.org-ogltrans is not installed, so not removed
Package openoffice.org-pdfimport is not installed, so not removed
Package openoffice.org-presentation-minimizer is not installed, so not removed
Package openoffice.org-presenter-console is not installed, so not removed
Package openoffice.org-report-builder is not installed, so not removed
Package openoffice.org-sdbc-postgresql is not installed, so not removed
Package openoffice.org-starter-guide is not installed, so not removed
Package openoffice.org-style-andromeda is not installed, so not removed
Package openoffice.org-style-crystal is not installed, so not removed
Package openoffice.org-style-galaxy is not installed, so not removed
Package openoffice.org-style-hicontrast is not installed, so not removed
Package openoffice.org-style-oxygen is not installed, so not removed
Package openoffice.org-style-tango is not installed, so not removed
Package openoffice.org-wiki-publisher is not installed, so not removed
Package openoffice.org-writer is not installed, so not removed
Package openoffice.org-writer2latex is not installed, so not removed
Package openoffice.org-writer2xhtml is not installed, so not removed
Package openoffice.org-zemberek is not installed, so not removed
Package python-openoffice is not installed, so not removed
Package openoffice.org-dtd-officedocument1.0 is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 aspell : Depends: dictionaries-common (> 0.40) but it is not going to be installed
 aspell-en : Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
 hunspell-en-ca : Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                           openoffice.org-updatedicts
 hunspell-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed
 hyphen-en-us : Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                         openoffice.org-updatedicts
 libreoffice-core : Depends: libreoffice-common (> 1:3.4.4) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
 myspell-en-au : Depends: dictionaries-common (>= 1.0) but it is not going to be installed
 myspell-en-gb : Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                          openoffice.org-updatedicts
 myspell-en-za : Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                          openoffice.org-updatedicts
 ooobasis3.3-core01 : Depends: openoffice.org-ure but it is not going to be installed
 wbritish : Depends: dictionaries-common (>= 0.20) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


so i try what i suggested and run apt-get -f install
and get...

```
nutmeg@nutmeg:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango libreoffice-style-crystal
  libreoffice-style-oxygen
The following NEW packages will be installed
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/16.9 MB of archives.
After this operation, 43.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 179950 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what am i doing wrong?

---

### Post by dino99 on 2012-02-20
do it from synaptic

(sudo apt-get install synaptic)
(sudo synaptic)

---

### Post by 73ckn797 on 2012-02-20
Use: ```
sudo apt-get purge openoffice
```
Then delete the folder for Open Office in your /home folder.

Installing Synaptic as mentioned will make the process easier for installing/removing software.

---

### Post by nutmegy on 2012-02-20
> **dino99 said:**
> do it from synaptic

(sudo apt-get install synaptic)
(sudo synaptic)

Tried that...

but now get

```
nutmeg@nutmeg:~$ sudo apt-get install synaptic
[sudo] password for nutmeg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libreoffice-core : Depends: libreoffice-common (> 1:3.4.4) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
 synaptic : Depends: libept1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by nutmegy on 2012-02-20
it doesnt help that the system thinks that libreoffice is still installed.... how can i make sure all has been removed for that then do a clean re-install?

---

### Post by nutmegy on 2012-02-20
sorted now... i think..

i deleted 

openoffice.org-debian-menus file ... plus deleted any other file with a similar name.. and all appears to be ok...

---

