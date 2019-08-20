## Keyword Searcher
#### C++ miniproject [CPP1_1]

&NewLine;

<font size="+2">Vinayak, Sarvesh, Bhavya, Harshali</font>

---?color=linear-gradient(0deg, white 80%, #5384AD 20%)

@snap[north span-50 h3-white]
### Key features
@snapend

@snap[south span-100]
@ul[list-spaced-bullets text-07]
- Console app to search for keywords in a directory
- Outputs the number of occurrences of each keyword
    - In each document of the search directory recursively
- Complex Queries: with AND, OR operators
- Exact match search using quotes
- Stemming
- Autocomplete suggestions for better search experience
- Horizontal collation of results
@ulend
@snapend

---

## Workflow design

+++?image=assets/img/chart1.png

+++?image=assets/img/chart2.png

+++?image=assets/img/chart3.png

---?color=linear-gradient(0deg, white 80%, #5384AD 20%)

@snap[north span-50 h3-white]
### Architecture
@snapend

@snap[south span-100]
@ul[list-spaced-bullets text-07]
- Fully object oriented structure.
- Classes and their utility
    - class **Start**: takes care of query input and autocompletion
    - class **DirParser**: recursively parses search directory
    - class **QueryParser**: validates query, creates *postFix* expression
        - uses a state machine to parse query accurately with all possible cases
    - class **Token**: each keyword in the above postFix expression is stored as a token
    - class **SearchAlgorithm**: base class of search algorithm implementations
        - class **KMP**: implements KMP search
        - class **AhoCorasick**: implements Aho-Corasick search
    - class **Displayer**: combines results and display it
    - class **Searcher**: main class
@ulend
@snapend

---

# Demo

---?color=linear-gradient(0deg, white 80%, #5384AD 20%)

@snap[north span-50 h3-white]
### Best practices
@snapend

@snap[center span-100]
@ul[list-spaced-bullets text-07]
- Use of *Smart Pointers*
    - Used `shared_ptr` wherever possible to avoid memory leak.
@ulend
@snapend

+++

@snap[center text-06]
```c++
typedef shared_ptr<Token> token_ptr;
typedef shared_ptr< vector<token_ptr> > vector_token_ptr;

token_ptr tokenPtrFactory(const string& value, int type)
{
    return make_shared<Token>(value, type);
}

vector_token_ptr vectorTokenPtrFactory()
{
    return make_shared< vector<token_ptr> >();
}
```
@snapend

---?color=linear-gradient(0deg, white 80%, #5384AD 20%)

@snap[north span-100 h3-white]
### Best practices
@snapend

@snap[center span-150]
@ul[list-spaced-bullets text-07]
- Use of *virtual functions*
    - class **SearchAlgorithm** has a pure virtual function **search()**
    - all classes which inherit from it must implement search function
- Error handling using **try - catch** blocks
- Neatly structured project files
    - header files in *\<root\>/include*
    - cpp files in *\<root\>/src*
    - used *cmake* to compile
 @ulend
@snapend

---?color=linear-gradient(0deg, white 80%, #5384AD 20%)

@snap[north span-100 h3-white]
### Future scope
@snapend

@snap[center span-150]
@ul[list-spaced-bullets text-07]
- Dynamically select between Aho-Corasick and KMP algorithm
    - Aho-Corasick is faster when the number of keywords in a search query increases
- Indexing of words
@ulend
@snapend

+++

@snap[center span-100]
<font size="+3">Our solution was chosen for its ease of use and implementation. With proper planning and division of work, we were able to concentrate on the quality of code and follow best practices.</font>
@snapend

---

## Thank you