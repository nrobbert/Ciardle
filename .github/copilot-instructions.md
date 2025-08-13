# Ciardle - Car Guessing Game

Ciardle is a browser-based car guessing game similar to Wordle, where players guess car makes and models from progressively revealed images. The game is built as a pure HTML/CSS/JavaScript static website with external API integrations.

**Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

## Working Effectively

### Bootstrap and Run the Application
- **NO BUILD REQUIRED** - This is a static HTML/CSS/JavaScript application
- Start local development server: `cd /home/runner/work/Ciardle/Ciardle && python3 -m http.server 8080`
- Server starts in under 100ms - set timeout to 5+ seconds minimum
- Access main game: `http://localhost:8080/ciardle.html`
- Access alternative version: `http://localhost:8080/Ciardle2.html`
- Access simple version: `http://localhost:8080/ciardle_old`

### External Dependencies
- **Tailwind CSS**: Loaded via CDN (`https://cdn.tailwindcss.com`) - may be blocked in restricted environments
- **Google Fonts**: Inter font family via CDN - may be blocked in restricted environments
- **Cloudinary**: Hosts game images and data files (`https://res.cloudinary.com/nickrobberts/`)
- **Google Gemini AI**: Generates hints (`https://generativelanguage.googleapis.com/`)
- **API Key Warning**: Gemini API key is embedded in JavaScript - replace for production deployment

### Game Files Overview
```
ciardle.html       - Main game (35KB, modern UI with full features)
Ciardle2.html      - Alternative layout (32KB, similar features)
ciardle_old        - Simple version (9KB, basic styling)
make.html          - Content creation tool (40KB)
Gemini_crop.html   - Image cropping utility (4KB)
Ciardlelogo.png    - Game logo
car*.jpg           - Sample car images
```

## Validation

### CRITICAL: Manual Testing Requirements
**ALWAYS test complete user workflows after making changes**:

1. **Basic Game Flow**:
   - Open `http://localhost:8080/ciardle.html`
   - Enter code "test" (default)
   - Click "Go!" button
   - **Expected**: Game loads with car image OR shows error if API blocked
   - Verify input fields become enabled/disabled appropriately

2. **Core Game Features**:
   - Enter make/model guesses in input fields
   - Click "Guess" button
   - Verify guess history table updates with tick/cross indicators
   - Test hint system by clicking "Get Hint ✨"
   - **Expected**: Game progresses through 5 image reveals OR ends on correct guess

3. **Image Interaction**:
   - Click on main car image to view in overlay
   - Click on previous guess images to view enlarged
   - Click outside overlay to close
   - **Expected**: Smooth image viewing experience

4. **Results System**:
   - Complete a game (win or lose)
   - Verify shareable results appear with proper formatting
   - Test "Copy Results" button functionality
   - **Expected**: Results contain game URL and emoji indicators

5. **Alternative Versions**:
   - Test `Ciardle2.html` for layout differences
   - Test `ciardle_old` for basic functionality
   - **Expected**: All versions should load and display properly

### Browser Compatibility Testing
- **ALWAYS test in browser environment** - cannot validate functionality through command line alone
- Modern browsers required for full feature support
- JavaScript must be enabled
- Local storage not required but enhances experience

### API Dependency Handling
- **Cloudinary Access**: Game requires internet access for car data and images
- **Gemini AI Access**: Hint feature requires API access
- **Expected Behavior When APIs Blocked**:
  - Game shows "Error loading car data" message
  - Input fields become disabled
  - Hint system shows error messages
  - This is NORMAL in restricted environments

## Common Tasks

### Repo Structure
```
ls -la /home/runner/work/Ciardle/Ciardle
.git/
Ciardle2.html      (32K) - Alternative game layout
Ciardlelogo.png    (82K) - Game logo image  
Gemini_crop.html   (4K)  - Image cropping tool
car.jpg + car1-5.jpg     - Sample car images
ciardle.html       (36K) - Main game file
ciardle_old        (9K)  - Simple game version
make.html          (40K) - Content creation tool
```

### Starting Development Server
```bash
cd /home/runner/work/Ciardle/Ciardle
python3 -m http.server 8080
# Server ready in ~50ms, access at http://localhost:8080/
```

### Testing Game Functionality
```bash
# Test server response (should complete in <10ms)
curl -I http://localhost:8080/ciardle.html

# Expected output: HTTP/1.0 200 OK
```

### File Validation
```bash
# Verify HTML files are valid
file *.html
# Expected: All should show "HTML document" 

# Check file sizes
du -sh *.html
# Expected: ciardle.html ~36K, Ciardle2.html ~32K, etc.
```

### Code Changes Guidelines
- **ALWAYS test in browser after HTML/CSS/JavaScript changes**
- **Main game logic**: Edit `ciardle.html` for full-featured version
- **Styling changes**: Modify embedded CSS or Tailwind classes
- **Game mechanics**: Update JavaScript functions in script tags
- **Alternative versions**: Consider impact on `Ciardle2.html` and `ciardle_old`

### Content Creation
- Use `make.html` for creating new game content
- Use `Gemini_crop.html` for image preparation  
- Images should be uploaded to Cloudinary with proper naming convention
- Game codes correspond to Cloudinary resource IDs

### Troubleshooting
- **Game won't load**: Check if HTTP server is running on port 8080
- **External resources blocked**: Expected in restricted environments - game UI should still render
- **JavaScript errors**: Check browser console for API failure messages
- **Image issues**: Verify car image files exist in repository
- **Styling problems**: Tailwind CSS may not load - fallback styles should apply

### Performance Expectations
- **HTML file loading**: < 10ms for local server
- **Image loading**: Depends on file size (car images 36KB-1.9MB)
- **Server startup**: ~50ms
- **API calls**: Variable based on network/restrictions
- **Game interaction**: Should be immediate for local content

### URL Parameters
- Game supports direct links: `ciardle.html?code=GAMECODE`
- **ALWAYS test URL parameter functionality** when modifying code entry system
- Verify auto-start behavior works correctly

Remember: This is a client-side application - most functionality depends on browser environment and external API access. Always validate changes through actual browser testing rather than command-line tools alone.