## Updates ##
  * **May 4, 2009** - added mouse wheel support via the **wheel** option


## Description ##
Carousel is a highly configurable Prototype.js extension that creates a nice way of presenting content that is logically broken into several pieces / steps / etc. It's:
  * **Lightweight** - 4.3 KB minified
  * **Cross-browser** - Tested on Internet Explorer 6/7/8, Firefox 2/3, Google Chrome, Opera 9.64

## Examples ##
Some of the most important features are presented on **[this page](http://dev.victorstanciu.ro/prototype/carousel/)**, the rest will be explained and discussed here.


## Requirements ##
Carousel.js needs both the [Prototype](http://www.prototypejs.org/) JavaScript framework and the [Script.aculo.us](http://script.aculo.us/) effects library to work.

## Usage ##
  * Download carousel.js or carousel-min.js
  * Include the script in your page, after the Prototype and Script.aculo.us libraries:
```
<script type="text/javascript" src="prototype.js"></script>
<script type="text/javascript" src="scriptaculous.js"></script>
<script type="text/javascript" src="carousel.js"></script>
```

### Markup ###
The minimum markup and styling are:
```
<div id="carousel-wrapper">
    <div id="carousel-content">
        <div class="slide"></div>
	<div class="slide"></div>
        ...
	<div class="slide"></div>
    </div>
</div>
```
```
#carousel-wrapper {
    width: 500px;
    height: 500px;
    overflow: hidden;
}
#carousel-content {
    width: 2500px;
}
#carousel-content .slide {
    float: left;
    width: 500px;
    height: 500px;
}
```
This will generate a 500x500px Carousel with horizontal movement. Switching to vertical movement is as simple as setting #carousel-content's width to 500px, the width of a single slide.

### Initialization ###
You initialize Carousel by:
```
new Carousel(wrapper, slides, triggers, {options});
```
For example, for the markup above:
```
new Carousel('carousel-wrapper', $$('#carousel-content .slide'), $$('a.carousel-control', 'a.carousel-jumper'));
```

### Triggers ###
There are two categories of elements that trigger the carousel's movement: the ones that trigger a direct jump to a selected slide (jump to slide "x"), and the ones that start a relative jump (jump to first/last/previous/next slide).
The combination of a trigger's **rel** and **class** attributes decide the Carousel's behavior. For example, clicking on:
```
<a href="javascript:" class="carousel-jumper" rel="slide-1">Jump to slide 1</a>
```
Will jump to the slide that has the id "slide-1". And:
```
<a href="javascript:" class="carousel-control" rel="prev">Previous slide</a>
```
Will jump to the previous slide. Available options for the **rel** attribute are **first**, **last**, **prev** and **next**.


## Available options ##
Options ar given as the last parameter in the initialization as hash: {option: value, option: value}
| **Options** | **Default** | **Description** |
|:------------|:------------|:----------------|
| duration    | 1           | The duration of a full jump |
| auto        | false       | When **true** the Carousel will move on it's own without needing triggers. Useful for slideshows |
| frequency   | 3           | When **auto** is **true**, this dictates how long a slides stays put before the next jump |
| visibleSlides | 1           | Even though multiple slides can be made visible at once by styling, this parameters is needed in some calculations |
| circular    | false       | By default when the first/last slide is reached, calling **prev**/**next** does nothing. If you want the effect to continue, you must do two things: Set the **circular** parameter **true** and **duplicate** the **first** slide in the HTML. It's the only way of giving the impression of a continous movement. |
| wheel       | true        | Whether or not to slide when using the mouse wheel over the slides |
| effect      | scroll      | You can choose between **scroll** and **fade**. When using **fade**, **circular** and duplicating the first slide is no longer necessary (see [Example 3](http://dev.victorstanciu.ro/prototype/carousel/) for the **fade** effect) |
| transition  | sinoidal    | The two supported transitions are **sinoidal** and **spring** (see [Example 2](http://dev.victorstanciu.ro/prototype/carousel/) for **spring**) |
| selectedClassName | carousel-selected | When triggering a jump by using a **carousel-jumper** trigger (jumps to specified slide), this CSS class is added to the trigger, to help you in visually highlighting it (see [Examples](http://dev.victorstanciu.ro/prototype/carousel/) for tab-navigation example) |
| beforeMove  | null        | User function that will be executed before a jump is started. For example: {beforeMove: function () { alert("Here i go!"); }} |
| afterMove   | null        | Just like **beforeMove**, only it's called after the move is completed |