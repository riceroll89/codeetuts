#### Encode and Decode TINYURL
> Note: This is a companion problem to the System Design problem: Design TinyURL.

TinyURL is a URL shortening service where you enter a URL such as https://leetcode.com/problems/design-tinyurl and it returns a short URL such as http://tinyurl.com/4e9iAk.

Design the encode and decode methods for the TinyURL service. There is no restriction on how your encode/decode algorithm should work. You just need to ensure that a URL can be encoded to a tiny URL and the tiny URL can be decoded to the original URL.

> This problem is solved using C++


```
class Solution {
public:

    // Encodes a URL to a shortened URL.
    string encode(string longUrl) {
        
    }

    // Decodes a shortened URL to its original URL.
    string decode(string shortUrl) {
        
    }
};

// Your Solution object will be instantiated and called as such:
// Solution solution;
// solution.decode(solution.encode(url)); 
```


> Solution Variable-length Encoding

```
public class Codec {

    String chars = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
    HashMap<String, String> map = new HashMap<>();
    int count = 1;

    public String getString() {
        int c = count;
        StringBuilder sb = new StringBuilder();
        while (c > 0) {
            c--;
            sb.append(chars.charAt(c % 62));
            c /= 62;
        }
        return sb.toString();
    }

    public String encode(String longUrl) {
        String key = getString();
        map.put(key, longUrl);
        return "http://tinyurl.com/" + key;
        count++;
    }

    public String decode(String shortUrl) {
        return map.get(shortUrl.replace("http://tinyurl.com/", ""));
    }
}
```
