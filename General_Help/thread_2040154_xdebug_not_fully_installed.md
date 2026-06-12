---
title: "xdebug not fully installed"
date: 2012-08-10
forum: General Help
---

### Post by daron300 on 2012-08-10
hi all.. i've installed xdebug, but when i run my application i saw that it established without interface ((
my test example

[PHP]
    function deep_end( $count ) {
        $count += 1;
        if ( $count < 48 ) {
                deep_end( $count );
        }
        else {
                trigger_error( "going off the deep end!" );
        }
    }
    deep_end( 1 );
[/PHP]xdebug return me  detailed error in inline format (( But i saw in xdebug.com before, that xdebug has a nice interface. Maybe it installed  wrong

---

