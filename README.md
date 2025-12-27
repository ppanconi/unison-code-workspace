# An Unison Workspace with appropriate context for codex AI agent

## How to use

- Instal Unison last `ucm` tool from Unison site [unison-lang.org](https://www.unison-lang.org/) with MCP support

- Add Unison MCP configuration to codex 
  in `~/.codex/config.toml` add 

```toml
[mcp_servers.unison]
command = "/path/to/ucm"
args = ["mcp"]
```
- start enjoy coding Unison with with codex support:

    Example:
    Adding boolean attribute support to @unison/xml library [text](https://share.unison-lang.org/@unison/xml). Before patching the library the tests in scratch.u fail. Make codex work.
    
    prompt: "I'm trying to use Unison library @unison/xml to parse html. But html is not xml so the parsing fails. In particular fails when an element has boolean attribute as <input disabled />. I'd like to modify the library to support boolean attributes. I see that the term 
    ```patterns.attribute : Pattern Text``` 
    can be a good starting point to change" 

    codex produces `boolean-attributes.u` automatically update unison terms and then all test pass
     
    22 | > Stream.toList (
           ⧩
           [ OpenTag 3 "b"
           , OpenTag 6 "d"
           , Attribute 9 "at1" "at1"
           , Attribute 13 "at2" "at2"
           , CloseTag 6 "d"
           , CloseTag 18 "b"
           ]
  
    44 | test> eventParser.tests.booleanAttributes.examples = test.verify do
    
    ✅ Passed Passed (cached)
  
    55 | test> eventParser.tests.booleanAttributes.props = test.verify do
    
    ✅ Passed Passed