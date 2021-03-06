

<!DOCTYPE HTML>
<html lang="" >
    <head>
        <meta charset="UTF-8">
        <meta content="text/html; charset=utf-8" http-equiv="Content-Type">
        <title>Data Structures · GitBook</title>
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="description" content="">
        <meta name="generator" content="GitBook 3.2.3">
<h1>Data Structures </h1>
<p>Data structures are basically just that - they are <em>structures</em> which can hold some <em>data</em> together. In other words, they are used to store a collection of related data.</p>
<p>There are four built-in data structures in Python - <em>list, tuple, dictionary and set</em>. We will see how to use each of them and how they make life easier for us.</p>
<h2 id="list">List</h2>
<p>A <code>list</code> is a data structure that holds an ordered collection of items i.e. you can store a <em>sequence</em> of items in a list. This is easy to imagine if you can think of a shopping list where you have a list of items to buy, except that you probably have each item on a separate line in your shopping list whereas in Python you put commas in between them.</p>
<p>The list of items should be enclosed in square brackets so that Python understands that you are specifying a list. Once you have created a list, you can add, remove or search for items in the list. Since we can add and remove items, we say that a list is a <em>mutable</em> data type i.e. this type can be altered.</p>
<h2 id="quick-introduction-to-objects-and-classes">Quick Introduction To Objects And Classes</h2>
<p>Although I&apos;ve been generally delaying the discussion of objects and classes till now, a little explanation is needed right now so that you can understand lists better. We will explore this topic in detail in a <a href="oop.html#oop">later chapter</a>.</p>
<p>A list is an example of usage of objects and classes. When we use a variable <code>i</code> and assign a value to it, say integer <code>5</code> to it, you can think of it as creating an <em>object</em> (i.e. instance) <code>i</code> of <em>class</em> (i.e. type) <code>int</code>. In fact, you can read <code>help(int)</code> to understand this better.</p>
<p>A class can also have <em>methods</em> i.e. functions defined for use with respect to that class only. You can use these pieces of functionality only when you have an object of that class. For example, Python provides an <code>append</code> method for the <code>list</code> class which allows you to add an item to the end of the list. For example, <code>mylist.append(&apos;an item&apos;)</code> will add that string to the list <code>mylist</code>. Note the use of dotted notation for accessing methods of the objects.</p>
<p>A class can also have <em>fields</em> which are nothing but variables defined for use with respect to that class only. You can use these variables/names only when you have an object of that class. Fields are also accessed by the dotted notation, for example, <code>mylist.field</code>.</p>
<p>Example (save as <code>ds_using_list.py</code>):</p>
<pre><code class="lang-python"><span class="hljs-comment"># This is my shopping list</span>
shoplist = [<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]

print(<span class="hljs-string">&apos;I have&apos;</span>, len(shoplist), <span class="hljs-string">&apos;items to purchase.&apos;</span>)

print(<span class="hljs-string">&apos;These items are:&apos;</span>, end=<span class="hljs-string">&apos; &apos;</span>)
<span class="hljs-keyword">for</span> item <span class="hljs-keyword">in</span> shoplist:
    print(item, end=<span class="hljs-string">&apos; &apos;</span>)

print(<span class="hljs-string">&apos;\nI also have to buy rice.&apos;</span>)
shoplist.append(<span class="hljs-string">&apos;rice&apos;</span>)
print(<span class="hljs-string">&apos;My shopping list is now&apos;</span>, shoplist)

print(<span class="hljs-string">&apos;I will sort my list now&apos;</span>)
shoplist.sort()
print(<span class="hljs-string">&apos;Sorted shopping list is&apos;</span>, shoplist)

print(<span class="hljs-string">&apos;The first item I will buy is&apos;</span>, shoplist[<span class="hljs-number">0</span>])
olditem = shoplist[<span class="hljs-number">0</span>]
<span class="hljs-keyword">del</span> shoplist[<span class="hljs-number">0</span>]
print(<span class="hljs-string">&apos;I bought the&apos;</span>, olditem)
print(<span class="hljs-string">&apos;My shopping list is now&apos;</span>, shoplist)
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_using_list.py
I have 4 items to purchase.
These items are: apple mango carrot banana
I also have to buy rice.
My shopping list is now [&apos;apple&apos;, &apos;mango&apos;, &apos;carrot&apos;, &apos;banana&apos;, &apos;rice&apos;]
I will sort my list now
Sorted shopping list is [&apos;apple&apos;, &apos;banana&apos;, &apos;carrot&apos;, &apos;mango&apos;, &apos;rice&apos;]
The first item I will buy is apple
I bought the apple
My shopping list is now [&apos;banana&apos;, &apos;carrot&apos;, &apos;mango&apos;, &apos;rice&apos;]
</code></pre>

<p><strong>How It Works</strong></p>
<p>The variable <code>shoplist</code> is a shopping list for someone who is going to the market. In <code>shoplist</code>, we only store strings of the names of the items to buy but you can add <em>any kind of object</em> to a list including numbers and even other lists.</p>
<p>We have also used the <code>for..in</code> loop to iterate through the items of the list. By now, you must have realised that a list is also a sequence. The speciality of sequences will be discussed in a <a href="#sequence">later section</a>.</p>
<p>Notice the use of the <code>end</code> parameter in the call to <code>print</code> function to indicate that we want to end the output with a space instead of the usual line break.</p>
<p>Next, we add an item to the list using the <code>append</code> method of the list object, as already discussed before. Then, we check that the item has been indeed added to the list by printing the contents of the list by simply passing the list to the <code>print</code> function which prints it neatly.</p>
<p>Then, we sort the list by using the <code>sort</code> method of the list. It is important to understand that this method affects the list itself and does not return a modified list - this is different from the way strings work. This is what we mean by saying that lists are <em>mutable</em> and that strings are <em>immutable</em>.</p>
<p>Next, when we finish buying an item in the market, we want to remove it from the list. We achieve this by using the <code>del</code> statement. Here, we mention which item of the list we want to remove and the <code>del</code> statement removes it from the list for us.  We specify that we want to remove the first item from the list and hence we use <code>del shoplist[0]</code> (remember that Python starts counting from 0).</p>
<p>If you want to know all the methods defined by the list object, see <code>help(list)</code> for details.</p>
<h2 id="tuple">Tuple</h2>
<p>Tuples are used to hold together multiple objects. Think of them as similar to lists, but without the extensive functionality that the list class gives you. One major feature of tuples is that they are <em>immutable</em> like strings i.e. you cannot modify tuples.</p>
<p>Tuples are defined by specifying items separated by commas within an optional pair of parentheses.</p>
<p>Tuples are usually used in cases where a statement or a user-defined function can safely assume that the collection of values (i.e. the tuple of values used) will not change.</p>
<p>Example (save as <code>ds_using_tuple.py</code>):</p>
<pre><code class="lang-python"><span class="hljs-comment"># I would recommend always using parentheses</span>
<span class="hljs-comment"># to indicate start and end of tuple</span>
<span class="hljs-comment"># even though parentheses are optional.</span>
<span class="hljs-comment"># Explicit is better than implicit.</span>
zoo = (<span class="hljs-string">&apos;python&apos;</span>, <span class="hljs-string">&apos;elephant&apos;</span>, <span class="hljs-string">&apos;penguin&apos;</span>)
print(<span class="hljs-string">&apos;Number of animals in the zoo is&apos;</span>, len(zoo))

new_zoo = <span class="hljs-string">&apos;monkey&apos;</span>, <span class="hljs-string">&apos;camel&apos;</span>, zoo    <span class="hljs-comment"># parentheses not required but are a good idea</span>
print(<span class="hljs-string">&apos;Number of cages in the new zoo is&apos;</span>, len(new_zoo))
print(<span class="hljs-string">&apos;All animals in new zoo are&apos;</span>, new_zoo)
print(<span class="hljs-string">&apos;Animals brought from old zoo are&apos;</span>, new_zoo[<span class="hljs-number">2</span>])
print(<span class="hljs-string">&apos;Last animal brought from old zoo is&apos;</span>, new_zoo[<span class="hljs-number">2</span>][<span class="hljs-number">2</span>])
print(<span class="hljs-string">&apos;Number of animals in the new zoo is&apos;</span>,
      len(new_zoo)<span class="hljs-number">-1</span>+len(new_zoo[<span class="hljs-number">2</span>]))
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_using_tuple.py
Number of animals in the zoo is 3
Number of cages in the new zoo is 3
All animals in new zoo are (&apos;monkey&apos;, &apos;camel&apos;, (&apos;python&apos;, &apos;elephant&apos;, &apos;penguin&apos;))
Animals brought from old zoo are (&apos;python&apos;, &apos;elephant&apos;, &apos;penguin&apos;)
Last animal brought from old zoo is penguin
Number of animals in the new zoo is 5
</code></pre>

<p><strong>How It Works</strong></p>
<p>The variable <code>zoo</code> refers to a tuple of items. We see that the <code>len</code> function can be used to get the length of the tuple. This also indicates that a tuple is a <a href="#sequence">sequence</a> as well.</p>
<p>We are now shifting these animals to a new zoo since the old zoo is being closed. Therefore, the <code>new_zoo</code> tuple contains some animals which are already there along with the animals brought over from the old zoo. Back to reality, note that a tuple within a tuple does not lose its identity.</p>
<p>We can access the items in the tuple by specifying the item&apos;s position within a pair of square brackets just like we did for lists. This is called the <em>indexing</em> operator. We access the third item in <code>new_zoo</code> by specifying <code>new_zoo[2]</code> and we access the third item within the third item in the <code>new_zoo</code> tuple by specifying <code>new_zoo[2][2]</code>. This is pretty simple once you&apos;ve understood the idiom.</p>
<blockquote>
<p><strong>Tuple with 0 or 1 items</strong></p>
<p>An empty tuple is constructed by an empty pair of parentheses such as <code>myempty = ()</code>. However, a tuple with a single item is not so simple. You have to specify it using a comma following the first (and only) item so that Python can differentiate between a tuple and a pair of parentheses surrounding the object in an expression i.e. you have to specify <code>singleton = (2 , )</code> if you mean you want a tuple containing the item <code>2</code>.</p>
</blockquote>
<!-- -->
<blockquote>
<p><strong>Note for Perl programmers</strong></p>
<p>A list within a list does not lose its identity i.e. lists are not flattened as in Perl. The same applies to a tuple within a tuple, or a tuple within a list, or a list within a tuple, etc. As far as Python is concerned, they are just objects stored using another object, that&apos;s all.</p>
</blockquote>
<h2 id="dictionary">Dictionary</h2>
<p>A dictionary is like an address-book where you can find the address or contact details of a person by knowing only his/her name i.e. we associate <em>keys</em> (name) with <em>values</em> (details). Note that the key must be unique just like you cannot find out the correct information if you have two persons with the exact same name.</p>
<p>Note that you can use only immutable objects (like strings) for the keys of a dictionary but you can use either immutable or mutable objects for the values of the dictionary.  This basically translates to say that you should use only simple objects for keys.</p>
<p>Pairs of keys and values are specified in a dictionary by using the notation <code>d = {key1 : value1, key2 : value2 }</code>. Notice that the key-value pairs are separated by a colon and the pairs are separated themselves by commas and all this is enclosed in a pair of curly braces.</p>
<p>Remember that key-value pairs in a dictionary are not ordered in any manner. If you want a particular order, then you will have to sort them yourself before using it.</p>
<p>The dictionaries that you will be using are instances/objects of the <code>dict</code> class.</p>
<p>Example (save as <code>ds_using_dict.py</code>):</p>
<pre><code class="lang-python"><span class="hljs-comment"># &apos;ab&apos; is short for &apos;a&apos;ddress&apos;b&apos;ook</span>

ab = {
    <span class="hljs-string">&apos;Swaroop&apos;</span>: <span class="hljs-string">&apos;swaroop@swaroopch.com&apos;</span>,
    <span class="hljs-string">&apos;Larry&apos;</span>: <span class="hljs-string">&apos;larry@wall.org&apos;</span>,
    <span class="hljs-string">&apos;Matsumoto&apos;</span>: <span class="hljs-string">&apos;matz@ruby-lang.org&apos;</span>,
    <span class="hljs-string">&apos;Spammer&apos;</span>: <span class="hljs-string">&apos;spammer@hotmail.com&apos;</span>
}

print(<span class="hljs-string">&quot;Swaroop&apos;s address is&quot;</span>, ab[<span class="hljs-string">&apos;Swaroop&apos;</span>])

<span class="hljs-comment"># Deleting a key-value pair</span>
<span class="hljs-keyword">del</span> ab[<span class="hljs-string">&apos;Spammer&apos;</span>]

print(<span class="hljs-string">&apos;\nThere are {} contacts in the address-book\n&apos;</span>.format(len(ab)))

<span class="hljs-keyword">for</span> name, address <span class="hljs-keyword">in</span> ab.items():
    print(<span class="hljs-string">&apos;Contact {} at {}&apos;</span>.format(name, address))

<span class="hljs-comment"># Adding a key-value pair</span>
ab[<span class="hljs-string">&apos;Guido&apos;</span>] = <span class="hljs-string">&apos;guido@python.org&apos;</span>

<span class="hljs-keyword">if</span> <span class="hljs-string">&apos;Guido&apos;</span> <span class="hljs-keyword">in</span> ab:
    print(<span class="hljs-string">&quot;\nGuido&apos;s address is&quot;</span>, ab[<span class="hljs-string">&apos;Guido&apos;</span>])
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_using_dict.py
Swaroop&apos;s address is swaroop@swaroopch.com

There are 3 contacts in the address-book

Contact Swaroop at swaroop@swaroopch.com
Contact Matsumoto at matz@ruby-lang.org
Contact Larry at larry@wall.org

Guido&apos;s address is guido@python.org
</code></pre>

<p><strong>How It Works</strong></p>
<p>We create the dictionary <code>ab</code> using the notation already discussed. We then access key-value pairs by specifying the key using the indexing operator as discussed in the context of lists and tuples. Observe the simple syntax.</p>
<p>We can delete key-value pairs using our old friend - the <code>del</code> statement. We simply specify the dictionary and the indexing operator for the key to be removed and pass it to the <code>del</code> statement. There is no need to know the value corresponding to the key for this operation.</p>
<p>Next, we access each key-value pair of the dictionary using the <code>items</code> method of the dictionary which returns a list of tuples where each tuple contains a pair of items - the key followed by the value. We retrieve this pair and assign it to the variables <code>name</code> and <code>address</code> correspondingly for each pair using the <code>for..in</code> loop and then print these values in the for-block.</p>
<p>We can add new key-value pairs by simply using the indexing operator to access a key and assign that value, as we have done for Guido in the above case.</p>
<p>We can check if a key-value pair exists using the <code>in</code> operator.</p>
<p>For the list of methods of the <code>dict</code> class, see <code>help(dict)</code>.</p>
<blockquote>
<p><strong>Keyword Arguments and Dictionaries</strong></p>
<p>If you have used keyword arguments in your functions, you have already used dictionaries! Just think about it - the key-value pair is specified by you in the parameter list of the function definition and when you access variables within your function, it is just a key access of a dictionary (which is called the <em>symbol table</em> in compiler design terminology).</p>
</blockquote>
<h2 id="sequence">Sequence</h2>
<p>Lists, tuples and strings are examples of sequences, but what are sequences and what is so special about them?</p>
<p>The major features are <em>membership tests</em>, (i.e. the <code>in</code> and <code>not in</code> expressions) and <em>indexing operations</em>, which allow us to fetch a particular item in the sequence directly.</p>
<p>The three types of sequences mentioned above - lists, tuples and strings, also have a <em>slicing</em> operation which allows us to retrieve a slice of the sequence i.e. a part of the sequence.</p>
<p>Example (save as <code>ds_seq.py</code>):</p>
<pre><code class="lang-python">shoplist = [<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]
name = <span class="hljs-string">&apos;swaroop&apos;</span>

<span class="hljs-comment"># Indexing or &apos;Subscription&apos; operation #</span>
print(<span class="hljs-string">&apos;Item 0 is&apos;</span>, shoplist[<span class="hljs-number">0</span>])
print(<span class="hljs-string">&apos;Item 1 is&apos;</span>, shoplist[<span class="hljs-number">1</span>])
print(<span class="hljs-string">&apos;Item 2 is&apos;</span>, shoplist[<span class="hljs-number">2</span>])
print(<span class="hljs-string">&apos;Item 3 is&apos;</span>, shoplist[<span class="hljs-number">3</span>])
print(<span class="hljs-string">&apos;Item -1 is&apos;</span>, shoplist[<span class="hljs-number">-1</span>])
print(<span class="hljs-string">&apos;Item -2 is&apos;</span>, shoplist[<span class="hljs-number">-2</span>])
print(<span class="hljs-string">&apos;Character 0 is&apos;</span>, name[<span class="hljs-number">0</span>])

<span class="hljs-comment"># Slicing on a list #</span>
print(<span class="hljs-string">&apos;Item 1 to 3 is&apos;</span>, shoplist[<span class="hljs-number">1</span>:<span class="hljs-number">3</span>])
print(<span class="hljs-string">&apos;Item 2 to end is&apos;</span>, shoplist[<span class="hljs-number">2</span>:])
print(<span class="hljs-string">&apos;Item 1 to -1 is&apos;</span>, shoplist[<span class="hljs-number">1</span>:<span class="hljs-number">-1</span>])
print(<span class="hljs-string">&apos;Item start to end is&apos;</span>, shoplist[:])

<span class="hljs-comment"># Slicing on a string #</span>
print(<span class="hljs-string">&apos;characters 1 to 3 is&apos;</span>, name[<span class="hljs-number">1</span>:<span class="hljs-number">3</span>])
print(<span class="hljs-string">&apos;characters 2 to end is&apos;</span>, name[<span class="hljs-number">2</span>:])
print(<span class="hljs-string">&apos;characters 1 to -1 is&apos;</span>, name[<span class="hljs-number">1</span>:<span class="hljs-number">-1</span>])
print(<span class="hljs-string">&apos;characters start to end is&apos;</span>, name[:])
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_seq.py
Item 0 is apple
Item 1 is mango
Item 2 is carrot
Item 3 is banana
Item -1 is banana
Item -2 is carrot
Character 0 is s
Item 1 to 3 is [&apos;mango&apos;, &apos;carrot&apos;]
Item 2 to end is [&apos;carrot&apos;, &apos;banana&apos;]
Item 1 to -1 is [&apos;mango&apos;, &apos;carrot&apos;]
Item start to end is [&apos;apple&apos;, &apos;mango&apos;, &apos;carrot&apos;, &apos;banana&apos;]
characters 1 to 3 is wa
characters 2 to end is aroop
characters 1 to -1 is waroo
characters start to end is swaroop
</code></pre>

<p><strong>How It Works</strong></p>
<p>First, we see how to use indexes to get individual items of a sequence. This is also referred to as the <em>subscription operation</em>. Whenever you specify a number to a sequence within square brackets as shown above, Python will fetch you the item corresponding to that position in the sequence. Remember that Python starts counting numbers from 0. Hence, <code>shoplist[0]</code> fetches the first item and <code>shoplist[3]</code> fetches the fourth item in the <code>shoplist</code> sequence.</p>
<p>The index can also be a negative number, in which case, the position is calculated from the end of the sequence. Therefore, <code>shoplist[-1]</code> refers to the last item in the sequence and <code>shoplist[-2]</code> fetches the second last item in the sequence.</p>
<p>The slicing operation is used by specifying the name of the sequence followed by an optional pair of numbers separated by a colon within square brackets. Note that this is very similar to the indexing operation you have been using till now. Remember the numbers are optional but the colon isn&apos;t.</p>
<p>The first number (before the colon) in the slicing operation refers to the position from where the slice starts and the second number (after the colon) indicates where the slice will stop at. If the first number is not specified, Python will start at the beginning of the sequence. If the second number is left out, Python will stop at the end of the sequence. Note that the slice returned <em>starts</em> at the start position and will end just before the <em>end</em> position i.e. the start position is included but the end position is excluded from the sequence slice.</p>
<p>Thus, <code>shoplist[1:3]</code> returns a slice of the sequence starting at position 1, includes position 2 but stops at position 3 and therefore a <em>slice</em> of two items is returned.  Similarly, <code>shoplist[:]</code> returns a copy of the whole sequence.</p>
<p>You can also do slicing with negative positions. Negative numbers are used for positions from the end of the sequence. For example, <code>shoplist[:-1]</code> will return a slice of the sequence which excludes the last item of the sequence but contains everything else.</p>
<p>You can also provide a third argument for the slice, which is the <em>step</em> for the slicing (by default, the step size is 1):</p>
<pre><code class="lang-python"><span class="hljs-meta">&gt;&gt;&gt; </span>shoplist = [<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]
<span class="hljs-meta">&gt;&gt;&gt; </span>shoplist[::<span class="hljs-number">1</span>]
[<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]
<span class="hljs-meta">&gt;&gt;&gt; </span>shoplist[::<span class="hljs-number">2</span>]
[<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>]
<span class="hljs-meta">&gt;&gt;&gt; </span>shoplist[::<span class="hljs-number">3</span>]
[<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]
<span class="hljs-meta">&gt;&gt;&gt; </span>shoplist[::<span class="hljs-number">-1</span>]
[<span class="hljs-string">&apos;banana&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;apple&apos;</span>]
</code></pre>
<p>Notice that when the step is 2, we get the items with position 0, 2,... When the step size is 3, we get the items with position 0, 3, etc.</p>
<p>Try various combinations of such slice specifications using the Python interpreter interactively i.e. the prompt so that you can see the results immediately. The great thing about sequences is that you can access tuples, lists and strings all in the same way!</p>
<h2 id="set">Set</h2>
<p>Sets are <em>unordered</em> collections of simple objects. These are used when the existence of an object in a collection is more important than the order or how many times it occurs.</p>
<p>Using sets, you can test for membership, whether it is a subset of another set, find the intersection between two sets, and so on.</p>
<pre><code class="lang-python"><span class="hljs-meta">&gt;&gt;&gt; </span>bri = set([<span class="hljs-string">&apos;brazil&apos;</span>, <span class="hljs-string">&apos;russia&apos;</span>, <span class="hljs-string">&apos;india&apos;</span>])
<span class="hljs-meta">&gt;&gt;&gt; </span><span class="hljs-string">&apos;india&apos;</span> <span class="hljs-keyword">in</span> bri
<span class="hljs-keyword">True</span>
<span class="hljs-meta">&gt;&gt;&gt; </span><span class="hljs-string">&apos;usa&apos;</span> <span class="hljs-keyword">in</span> bri
<span class="hljs-keyword">False</span>
<span class="hljs-meta">&gt;&gt;&gt; </span>bric = bri.copy()
<span class="hljs-meta">&gt;&gt;&gt; </span>bric.add(<span class="hljs-string">&apos;china&apos;</span>)
<span class="hljs-meta">&gt;&gt;&gt; </span>bric.issuperset(bri)
<span class="hljs-keyword">True</span>
<span class="hljs-meta">&gt;&gt;&gt; </span>bri.remove(<span class="hljs-string">&apos;russia&apos;</span>)
<span class="hljs-meta">&gt;&gt;&gt; </span>bri &amp; bric <span class="hljs-comment"># OR bri.intersection(bric)</span>
{<span class="hljs-string">&apos;brazil&apos;</span>, <span class="hljs-string">&apos;india&apos;</span>}
</code></pre>
<p><strong>How It Works</strong></p>
<p>If you remember basic set theory mathematics from school, then this example is fairly self-explanatory.  But if not, you can google &quot;set theory&quot; and &quot;Venn diagram&quot; to better understand our use of sets in Python.</p>
<h2 id="references">References</h2>
<p>When you create an object and assign it to a variable, the variable only <em>refers</em> to the object and does not represent the object itself!  That is, the variable name points to that part of your computer&apos;s memory where the object is stored. This is called <em>binding</em> the name to the object.</p>
<p>Generally, you don&apos;t need to be worried about this, but there is a subtle effect due to references which you need to be aware of:</p>
<p>Example (save as <code>ds_reference.py</code>):</p>
<pre><code class="lang-python">print(<span class="hljs-string">&apos;Simple Assignment&apos;</span>)
shoplist = [<span class="hljs-string">&apos;apple&apos;</span>, <span class="hljs-string">&apos;mango&apos;</span>, <span class="hljs-string">&apos;carrot&apos;</span>, <span class="hljs-string">&apos;banana&apos;</span>]
<span class="hljs-comment"># mylist is just another name pointing to the same object!</span>
mylist = shoplist

<span class="hljs-comment"># I purchased the first item, so I remove it from the list</span>
<span class="hljs-keyword">del</span> shoplist[<span class="hljs-number">0</span>]

print(<span class="hljs-string">&apos;shoplist is&apos;</span>, shoplist)
print(<span class="hljs-string">&apos;mylist is&apos;</span>, mylist)
<span class="hljs-comment"># Notice that both shoplist and mylist both print</span>
<span class="hljs-comment"># the same list without the &apos;apple&apos; confirming that</span>
<span class="hljs-comment"># they point to the same object</span>

print(<span class="hljs-string">&apos;Copy by making a full slice&apos;</span>)
<span class="hljs-comment"># Make a copy by doing a full slice</span>
mylist = shoplist[:]
<span class="hljs-comment"># Remove first item</span>
<span class="hljs-keyword">del</span> mylist[<span class="hljs-number">0</span>]

print(<span class="hljs-string">&apos;shoplist is&apos;</span>, shoplist)
print(<span class="hljs-string">&apos;mylist is&apos;</span>, mylist)
<span class="hljs-comment"># Notice that now the two lists are different</span>
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_reference.py
Simple Assignment
shoplist is [&apos;mango&apos;, &apos;carrot&apos;, &apos;banana&apos;]
mylist is [&apos;mango&apos;, &apos;carrot&apos;, &apos;banana&apos;]
Copy by making a full slice
shoplist is [&apos;mango&apos;, &apos;carrot&apos;, &apos;banana&apos;]
mylist is [&apos;carrot&apos;, &apos;banana&apos;]
</code></pre>

<p><strong>How It Works</strong></p>
<p>Most of the explanation is available in the comments.</p>
<p>Remember that if you want to make a copy of a list or such kinds of sequences or complex objects (not simple <em>objects</em> such as integers), then you have to use the slicing operation to make a copy. If you just assign the variable name to another name, both of them will &apos;&apos;refer&apos;&apos; to the same object and this could be trouble if you are not careful.</p>
<blockquote>
<p><strong>Note for Perl programmers</strong></p>
<p>Remember that an assignment statement for lists does <strong>not</strong> create a copy. You have to use slicing operation to make a copy of the sequence.</p>
</blockquote>
<h2 id="more-strings">More About Strings </h2>
<p>We have already discussed strings in detail earlier. What more can there be to know?  Well, did you know that strings are also objects and have methods which do everything from checking part of a string to stripping spaces?  In fact, you&apos;ve already been using a string method... the <code>format</code> method!</p>
<p>The strings that you use in programs are all objects of the class <code>str</code>.  Some useful methods of this class are demonstrated in the next example. For a complete list of such methods, see <code>help(str)</code>.</p>
<p>Example (save as <code>ds_str_methods.py</code>):</p>
<pre><code class="lang-python"><span class="hljs-comment"># This is a string object</span>
name = <span class="hljs-string">&apos;Swaroop&apos;</span>

<span class="hljs-keyword">if</span> name.startswith(<span class="hljs-string">&apos;Swa&apos;</span>):
    print(<span class="hljs-string">&apos;Yes, the string starts with &quot;Swa&quot;&apos;</span>)

<span class="hljs-keyword">if</span> <span class="hljs-string">&apos;a&apos;</span> <span class="hljs-keyword">in</span> name:
    print(<span class="hljs-string">&apos;Yes, it contains the string &quot;a&quot;&apos;</span>)

<span class="hljs-keyword">if</span> name.find(<span class="hljs-string">&apos;war&apos;</span>) != <span class="hljs-number">-1</span>:
    print(<span class="hljs-string">&apos;Yes, it contains the string &quot;war&quot;&apos;</span>)

delimiter = <span class="hljs-string">&apos;_*_&apos;</span>
mylist = [<span class="hljs-string">&apos;Brazil&apos;</span>, <span class="hljs-string">&apos;Russia&apos;</span>, <span class="hljs-string">&apos;India&apos;</span>, <span class="hljs-string">&apos;China&apos;</span>]
print(delimiter.join(mylist))
</code></pre>

<p>Output:</p>
<pre><code>$ python ds_str_methods.py
Yes, the string starts with &quot;Swa&quot;
Yes, it contains the string &quot;a&quot;
Yes, it contains the string &quot;war&quot;
Brazil_*_Russia_*_India_*_China
</code></pre>

<p><strong>How It Works</strong></p>
<p>Here, we see a lot of the string methods in action. The <code>startswith</code> method is used to find out whether the string starts with the given string. The <code>in</code> operator is used to check if a given string is a part of the string.</p>
<p>The <code>find</code> method is used to locate the position of the given substring within the string; <code>find</code> returns -1 if it is unsuccessful in finding the substring. The <code>str</code> class also has a neat method to <code>join</code> the items of a sequence with the string acting as a delimiter between each item of the sequence and returns a bigger string generated from this.</p>
<h2 id="summary">Summary</h2>
<p>We have explored the various built-in data structures of Python in detail. These data structures will be essential for writing programs of reasonable size.</p>
<p>Now that we have a lot of the basics of Python in place, we will next see how to design and write a real-world Python program.</p>
</html>

