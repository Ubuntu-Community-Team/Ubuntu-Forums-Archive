---
title: "getting error message at web page"
date: 2010-12-20
forum: General Help
---

### Post by lex1 on 2010-12-20
any feedback on the error message below please:


Exception Object
(
    [message:protected] => Could not connect to host
    [string:private] => 
    [code:protected] => 32
    [file:protected] => /srv/vbox/lib/vboxconnector.php
    [line:protected] => 111
    [trace:private] => Array
        (
            [0] => Array
                (
                    [file] => /srv/vbox/lib/vboxconnector.php
                    [line] => 1821
                    [function] => __vboxwebsrvConnect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )

                )

            [1] => Array
                (
                    [file] => /srv/vbox/lib/vboxconnector.php
                    [line] => 218
                    [function] => getMediumsCached
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                            [0] => Array
                                (
                                    [fn] => getMediums
                                )

                            [1] => Array
                                (
                                    [data] => 
                                    [errors] => Array
                                        (
                                        )

                                    [persist] => Array
                                        (
                                        )

                                )

                        )

                )

            [2] => Array
                (
                    [function] => __call
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                            [0] => getMediums
                            [1] => Array
                                (
                                    [0] => Array
                                        (
                                            [fn] => getMediums
                                        )

                                    [1] => Array
                                        (
                                            [0] => Array
                                                (
                                                    [data] => 
                                                    [errors] => Array
                                                        (
                                                        )

                                                    [persist] => Array
                                                        (
                                                        )

                                                )

                                        )

                                )

                        )

                )

            [3] => Array
                (
                    [file] => /srv/vbox/lib/ajax.php
                    [line] => 93
                    [function] => getMediums
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                            [0] => Array
                                (
                                    [fn] => getMediums
                                )

                            [1] => Array
                                (
                                    [0] => Array
                                        (
                                            [data] => 
                                            [errors] => Array
                                                (
                                                )

                                            [persist] => Array
                                                (
                                                )

                                        )

                                )

                        )

                )

        )

)


lex1;)
ps not sure why the smiles are in there

---

### Post by searchfgold6789 on 2010-12-20
I would guess that it is a problem with the website, not with your computer.
(To avoid getting those smilies, use Code Tags)

---

### Post by lex1 on 2010-12-21
this on my website installed by myself

lex1

---

