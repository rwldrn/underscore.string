# Underscore.string #

Idea: Esa-Matti Suuronen (esa-matti aet suuronen dot org)

Authors: Esa-Matti Suuronen, Edward Tsech

Javascript lacks complete string manipulation operations.
This an attempt to fill that cap. List of buildin methods can be found
for example from [Dive Into JavaScript][d].

[d]: http://www.diveintojavascript.com/core-javascript-reference/the-string-object


As name states this an extension for [Underscore.js][u], but it can be used
independently from **_s**-global variable. But with Underscore.js you can
use Object-Oriented style and chaining:

[u]: http://documentcloud.github.com/underscore/

    _("   epeli  ").chain().trim().capitalize().value()
    => "Epeli"

## Node.js installation ##

**npm package**

    npm install underscore.string

**Standalone usage**:

    var _s = require('undescore.string');

**Integrate with Underscore.js**:

    var _  = require('underscore');
    _.mixin(require('underscore.string'));

## String Functions ##

**capitalize** _.capitalize(string)

Converts first letter of the string to uppercase.

    _.capitalize("epeli")
    => "Epeli"

**chop** _.chop(string, step)

    _.chop('whitespace', 3)
    => ['whi','tes','pac','e']

**clean** _.clean(str)

Compress some whitespaces to one.

    _.clean(" foo    bar   ")
    => 'foo bar'

**chars** _.chars(str)

    _.chars('Hello')
    => ['H','e','l','l','o']

**includes** _.includes(string, substring)

Tests if string contains a substring.

    _.includes("foobar", "ob")
    => true

**count** _.count(string, substring)

    _('Hello world').count('l')
    => 3

**escapeHTML** _.escapeHTML(string)

Converts HTML special characters to their entity equivalents.

    _('<div>Blah blah blah</div>').escapeHTML();
    => '&lt;div&gt;Blah blah blah&lt;/div&gt;'

**unescapeHTML** _.unescapeHTML(string)

Converts entity characters to HTML equivalents.

    _('&lt;div&gt;Blah blah blah&lt;/div&gt;').unescapeHTML();
    => '<div>Blah blah blah</div>'

**insert** _.insert(string, index, substing)

    _('Hello ').insert(6, 'world')
    => 'Hello world'

**join** _.join(separator, *strings)

Joins strings together with given separator

    _.join(" ", "foo", "bar")
    => "foo bar"

**lines** _.lines(str)

    _.lines("Hello\nWorld")
    => ["Hello", "World"]

**reverse**

This functions has been removed, because this function override underscore.js 'reverse'.
But now you can do that:

    _("foobar").chars().reverse().join('')

**splice**  _.splice(string, index, howmany, substring)

Like a array splice.

    _('https://edtsech@bitbucket.org/edtsech/underscore.strings').splice(30, 7, 'epeli')
    => 'https://edtsech@bitbucket.org/epeli/underscore.strings'

**startsWith** _.startsWith(string, starts)

This method checks whether string starts with starts.

    _("image.gif").startsWith("image")
    => true

**endsWith** _.endsWith(string, ends)

This method checks whether string ends with ends.

    _("image.gif").endsWith("gif")
    => true

**succ**  _.succ(str)

Returns the successor to str.

    _('a').succ()
    => 'b'

    _('A').succ()
    => 'B'

**supplant**

Supplant function was removed, use Underscore.js [template function][p].

[p]: http://documentcloud.github.com/underscore/#template

**strip** alias for *trim*

**lstrip** alias for *ltrim*

**rstrip** alias for *rtrim*

**titleize** _.titleize(string)

    _('my name is epeli').titleize()
    => 'My Name Is Epeli'

**trim** _.trim(string, [characters])

trims defined characters from begining and ending of the string.
Defaults to whitespace characters.

    _.trim("  foobar   ")
    => "foobar"

    _.trim("_-foobar-_", "_-")
    => "foobar"


**ltrim** _.ltrim(string, [characters])

Left trim. Similar to trim, but only for left side.


**rtrim** _.rtrim(string, [characters])

Left trim. Similar to trim, but only for right side.

**truncate** _.truncate(string, length, truncateString)

    _('Hello world').truncate(5)
    => 'Hello...'

**words** _.words(str, delimiter=" ")

Split string by delimiter (String or RegExp), ' ' by default.

    _.words("I love you")
    => ["I","love","you"]

    _.words("I_love_you", "_")
    => ["I","love","you"]

    _.words("I-love-you", /-/)
    => ["I","love","you"]

**sprintf** _.sprintf(string format, *arguments)

C like string formatting.
Credits goes to [Alexandru Marasteanu][o].
For more detailed documentation, see the [original page][o].

[o]: http://www.diveintojavascript.com/projects/sprintf-for-javascript

    _.sprintf("%.1f", 1.17)
    "1.2"

## Roadmap ##

* Resolve problem with function names crossing between libraries (include, contains and etc).

Any suggestions or bug reports are welcome. Just email me or more preferably open an issue.

## Changelog ##

### 1.1.2 ###

* Created functions: lines, chars, words functions

### 1.0.2 ###

* Created integration test suite with underscore.js 1.1.4 (now it's absolutely compatible)
* Removed 'reverse' function, because this function override underscore.js 'reverse'

## Contributors list##

*  Esa-Matti Suuronen <esa-matti@suuronen.org> (http://esa-matti.suuronen.org/),
*  Edward Tsech <edtsech@gmail.com>,
*  Sasha Koss <kossnocorp@gmail.com> (http://koss.nocorp.me/),
*  Vladimir Dronnikov <dronnikov@gmail.com>

## Licence ##

[MIT Licence][mit]
[mit]: http://www.opensource.org/licenses/mit-license.php
