---
layout: post
title:  "Intelij surround with"
date:   2015-07-01 13:49:57
categories: jekyll update
---
I recently refactored some code and had a lots of instances where I need to change code from

```
 final Level close = levelService.get(esContract, 1700.00);
```

to

```
 final Level close = levelService.get(esContract, new BigDecimal("1700.00"));
```

Normally structural find/replace or regex find/replace works well but not in this case. So time to learn how to write 'surround with' Live Templates.

### Live Templates
Go to Live Templates in Preferences `cmd ,`. (Templates not Template)

####Now fill out all the fields

####Heading
Add an abbreviation `swbd`.

Write a description `Surround with BigDecimal`.

####Code
Create a new template and write your content.
```
new java.math.BigDecimal("$SELECTION$")
```

The `$SELECTION$` is the code you want to surround.

####Define the contexts.
In the `Java` section select `Expression`.
Use Qualified names.

####Options
Check `Short FQ names`. We want `java.math.BigDecimal` to appear as just `BigDecimal`.

For this example the other options aren't needed.

#### Editor
Back in the editor highlight the code you want to surround. Execute the live template shortcut `Cmd Option J`. 
Select your live template and enjoy saving a few keystrokes.
