<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>フラワーディスプレイ・プロフェッショナルの冒険</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Noto Sans JP', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .game-container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        .header {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            text-align: center;
            backdrop-filter: blur(10px);
        }
        
        .title {
            font-size: 2.5em;
            font-weight: 700;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #666;
            font-size: 1.1em;
            margin-bottom: 20px;
        }
        
        .progress-bar {
            width: 100%;
            height: 12px;
            background: #e0e0e0;
            border-radius: 6px;
            overflow: hidden;
            margin: 20px 0;
        }
        
        .progress {
            height: 100%;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4);
            border-radius: 6px;
            transition: width 0.5s ease;
        }
        
        .stats {
            display: flex;
            justify-content: space-around;
            margin-top: 15px;
        }
        
        .stat {
            text-align: center;
        }
        
        .stat-value {
            font-size: 1.5em;
            font-weight: 700;
            color: #4ecdc4;
        }
        
        .stat-label {
            font-size: 0.9em;
            color: #666;
        }
        
        .game-content {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            flex-grow: 1;
        }
        
        .chapter-intro {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .chapter-title {
            font-size: 1.8em;
            font-weight: 600;
            color: #4a5568;
            margin-bottom: 10px;
        }
        
        .character {
            font-size: 4em;
            margin: 20px 0;
        }
        
        .story-text {
            font-size: 1.1em;
            line-height: 1.6;
            color: #666;
            margin-bottom: 30px;
            padding: 20px;
            background: rgba(74, 85, 104, 0.05);
            border-radius: 10px;
        }
        
        .question {
            margin-bottom: 30px;
        }
        
        .question-text {
            font-size: 1.3em;
            font-weight: 500;
            color: #2d3748;
            margin-bottom: 20px;
            line-height: 1.5;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .option {
            padding: 20px;
            background: #f7fafc;
            border: 2px solid #e2e8f0;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.1em;
        }
        
        .option:hover {
            background: #edf2f7;
            border-color: #4ecdc4;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .option.selected {
            background: #4ecdc4;
            color: white;
            border-color: #4ecdc4;
        }
        
        .option.correct {
            background: #48bb78;
            color: white;
            border-color: #48bb78;
        }
        
        .option.incorrect {
            background: #f56565;
            color: white;
            border-color: #f56565;
        }
        
        .submit-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
            display: block;
            margin-left: auto;
            margin-right: auto;
        }
        
        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }
        
        .submit-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }
        
        .feedback {
            margin-top: 30px;
            padding: 25px;
            border-radius: 15px;
            display: none;
        }
        
        .feedback.correct {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
        }
        
        .feedback.incorrect {
            background: linear-gradient(135deg, #f56565, #e53e3e);
            color: white;
        }
        
        .feedback-title {
            font-size: 1.3em;
            font-weight: 600;
            margin-bottom: 15px;
        }
        
        .explanation {
            font-size: 1.1em;
            line-height: 1.6;
            margin-bottom: 15px;
        }
        
        .learning-point {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 10px;
            margin-top: 15px;
        }
        
        .next-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
            padding: 12px 25px;
            border-radius: 20px;
            font-size: 1em;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
        }
        
        .next-btn:hover {
            background: white;
            color: #4a5568;
        }
        
        .achievement {
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin: 20px 0;
            box-shadow: 0 10px 25px rgba(255, 215, 0, 0.3);
        }
        
        .badge {
            font-size: 3em;
            margin-bottom: 10px;
        }
        
        .final-results {
            text-align: center;
            padding: 30px;
        }
        
        .restart-btn {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            margin: 10px;
            transition: all 0.3s ease;
        }
        
        .restart-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }
        
        .weakness-report {
            background: #f7fafc;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border-left: 5px solid #4ecdc4;
        }
        
        .weakness-title {
            font-size: 1.3em;
            font-weight: 600;
            color: #2d3748;
            margin-bottom: 15px;
        }
        
        .weakness-item {
            margin: 10px 0;
            padding: 10px 15px;
            background: white;
            border-radius: 8px;
            border-left: 3px solid #ff6b6b;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="header">
            <h1 class="title">🌸 フラワーディスプレイ・プロフェッショナルの冒険 🌸</h1>
            <p class="subtitle">業務委託スタッフとしての知識と心構えを身につける旅</p>
            
            <div class="progress-bar">
                <div class="progress" id="progressBar"></div>
            </div>
            
            <div class="stats">
                <div class="stat">
                    <div class="stat-value" id="currentQuestion">1</div>
                    <div class="stat-label">現在の問題</div>
                </div>
                <div class="stat">
                    <div class="stat-value" id="score">0</div>
                    <div class="stat-label">スコア</div>
                </div>
                <div class="stat">
                    <div class="stat-value" id="level">見習い</div>
                    <div class="stat-label">レベル</div>
                </div>
            </div>
        </div>
        
        <div class="game-content" id="gameContent">
            <!-- ゲームコンテンツがここに挿入される -->
        </div>
    </div>

    <script>
        class ConductCodeGame {
            constructor() {
                this.currentQuestion = 0;
                this.score = 0;
                this.maxScore = 0;
                this.wrongAnswers = [];
                this.selectedAnswer = null;
                this.gameData = this.initializeGameData();
                this.init();
            }
            
            initializeGameData() {
                return {
                    chapters: [
                        {
                            title: "第1章：プロフェッショナルの心構え",
                            character: "🌱",
                            story: "あなたは新たにフラワーディスプレイの世界に足を踏み入れたプロフェッショナルです。美しい花々に囲まれた工房で、先輩たちとの関係性について学びましょう。",
                            questions: [0, 1, 2]
                        },
                        {
                            title: "第2章：コミュニケーションの秘訣",
                            character: "🗣️",
                            story: "現場では様々な人々と協力する必要があります。効果的なコミュニケーションの技術を身につけ、チームワークを高めましょう。",
                            questions: [3, 4, 5]
                        },
                        {
                            title: "第3章：困難な状況への対応",
                            character: "⚡",
                            story: "クリスマスシーズンの繁忙期が到来しました。予期せぬ問題が発生する中で、プロフェッショナルとしての真価が問われます。",
                            questions: [6, 7, 8]
                        },
                        {
                            title: "最終章：マスタープロフェッショナルへの道",
                            character: "👑",
                            story: "あなたの知識と経験が試される最終試験です。真のプロフェッショナルとして成長できるでしょうか？",
                            questions: [9]
                        }
                    ],
                    questions: [
                        {
                            text: "業務委託における関係性について、最も適切な表現はどれですか？",
                            options: [
                                "会社とスタッフの上下関係である",
                                "それぞれが専門性を持つ対等なパートナーシップである", 
                                "経験年数によって立場が決まる関係である"
                            ],
                            correct: 1,
                            difficulty: 1,
                            explanation: "業務委託では、お互いが専門性を尊重し合う対等なパートナーシップが基本となります。",
                            learningPoint: "💡 業務委託は雇用関係ではなく、専門的なサービスを提供する対等な関係です。相互尊重が成功の鍵となります。"
                        },
                        {
                            text: "現場でのコミュニケーションで最も重要なことは何ですか？",
                            options: [
                                "大きな声ではっきりと話す",
                                "冷静で穏やかな声量と丁寧な言葉遣い",
                                "自分の意見を強く主張する"
                            ],
                            correct: 1,
                            difficulty: 1,
                            explanation: "プロフェッショナルな現場では、冷静で丁寧なコミュニケーションが信頼関係を築きます。",
                            learningPoint: "🎯 声のトーンと言葉遣いは、あなたのプロフェッショナルさを表現する重要な要素です。"
                        },
                        {
                            text: "デザインや技術的な意見の相違がある場合の適切な対応はどれですか？",
                            options: [
                                "自分の意見を強く主張する",
                                "「別の方法も検討してみませんか？」などの提案型の表現を使う",
                                "黙って従う"
                            ],
                            correct: 1,
                            difficulty: 2,
                            explanation: "提案型の表現は相手を尊重しながら建設的な議論を促します。これにより創造的な解決策が生まれます。",
                            learningPoint: "🤝 対立ではなく協力的な問題解決により、より良い結果を生み出すことができます。"
                        },
                        {
                            text: "繁忙期で特に注意すべきことは何ですか？（批判的思考問題）",
                            options: [
                                "忙しいときこそ、いつも以上に声を掛け合い協力する",
                                "焦りや疲れがたまりやすいので冷静さを保つ", 
                                "時間がないので安全確認は簡単に済ませる"
                            ],
                            correct: 1,
                            difficulty: 3,
                            explanation: "繁忙期こそ冷静さが重要です。焦りは判断力を鈍らせ、品質や安全性の低下につながります。",
                            learningPoint: "⚖️ 忙しい時ほど基本に立ち返ることが、結果的に効率的で安全な作業につながります。"
                        },
                        {
                            text: "チーム内で意見の衝突が起きた時、プロフェッショナルとして最も重要な行動は？（応用問題）",
                            options: [
                                "経験の長い人の意見を優先する",
                                "多数決で決める",
                                "全員の意見を聞き、建設的な解決策を模索する"
                            ],
                            correct: 2,
                            difficulty: 4,
                            explanation: "真のプロフェッショナルは、異なる視点を統合して最適解を見つける能力を持ちます。",
                            learningPoint: "🧩 多様な意見を統合することで、一人では思いつかない革新的なアイデアが生まれます。"
                        },
                        {
                            text: "クライアントの前でのチームとしての振る舞いで最も重要なことは？",
                            options: [
                                "個人の意見を強く主張する",
                                "チームとしての一貫性を保ち、協力的な態度を示す",
                                "他のスタッフの問題点を指摘する"
                            ],
                            correct: 1,
                            difficulty: 2,
                            explanation: "クライアントに対してはチーム一丸となった信頼できる姿勢を示すことが重要です。",
                            learningPoint: "👥 チームの結束力は、クライアントの信頼と満足度に直結します。"
                        },
                        {
                            text: "現場で予期せぬ状況が発生した場合の最適な対応順序は？（論理的思考問題）",
                            options: [
                                "一人で解決を試み、だめなら報告する",
                                "冷静に状況を把握し、必要に応じて速やかに報告・相談する",
                                "他の人に任せて自分は通常業務を続ける"
                            ],
                            correct: 1,
                            difficulty: 4,
                            explanation: "まず冷静な状況把握、そして適切なタイミングでの報告・相談が問題解決の鉄則です。",
                            learningPoint: "🎯 問題解決のプロセス：①状況把握 ②影響評価 ③適切な報告 ④協力的解決"
                        },
                        {
                            text: "プロフェッショナルとして最も重要な基盤となることは？",
                            options: [
                                "約束の遵守と自己管理の徹底",
                                "自分の意見を最優先する",
                                "他人の意見に常に従う"
                            ],
                            correct: 0,
                            difficulty: 3,
                            explanation: "信頼されるプロフェッショナルの基盤は、約束を守り、自分自身を適切に管理する能力です。",
                            learningPoint: "🏛️ 信頼は全てのプロフェッショナル関係の基礎となる最も重要な資産です。"
                        },
                        {
                            text: "業務上の問題や悩みがある場合の対応として最も建設的なものは？",
                            options: [
                                "一人で抱え込んで解決策を見つける",
                                "同僚に愚痴として相談する",
                                "遠慮なく会社に相談し、建設的な解決を求める"
                            ],
                            correct: 2,
                            difficulty: 3,
                            explanation: "問題の早期発見と適切な相談は、より大きな問題を防ぎ、組織全体の改善につながります。",
                            learningPoint: "🔄 オープンなコミュニケーションは組織の学習と成長を促進します。"
                        },
                        {
                            text: "【統合問題】長年の経験を持つプロフェッショナルとして、新しいメンバーとの協業で最も重要なのは？",
                            options: [
                                "自分の経験と知識を一方的に教える",
                                "相手の専門性を尊重し、互いの強みを活かした協力関係を築く",
                                "経験の差を明確にして指導的立場を確立する"
                            ],
                            correct: 1,
                            difficulty: 5,
                            explanation: "真のプロフェッショナルは、経験に関係なく他者の専門性を認め、相互学習の機会として協業を捉えます。",
                            learningPoint: "🌟 経験豊富なプロフェッショナルほど、謙虚さと学習意欲を持ち続けることで、さらなる成長を遂げられます。"
                        }
                    ]
                };
            }
            
            init() {
                this.updateProgress();
                this.showChapterIntro();
            }
            
            getCurrentChapter() {
                for (let chapter of this.gameData.chapters) {
                    if (chapter.questions.includes(this.currentQuestion)) {
                        return chapter;
                    }
                }
                return this.gameData.chapters[0];
            }
            
            showChapterIntro() {
                const chapter = this.getCurrentChapter();
                const isNewChapter = chapter.questions[0] === this.currentQuestion;
                
                if (isNewChapter) {
                    const content = `
                        <div class="chapter-intro">
                            <h2 class="chapter-title">${chapter.title}</h2>
                            <div class="character">${chapter.character}</div>
                            <div class="story-text">${chapter.story}</div>
                            <button class="submit-btn" onclick="game.showQuestion()">冒険を開始する</button>
                        </div>
                    `;
                    document.getElementById('gameContent').innerHTML = content;
                } else {
                    this.showQuestion();
                }
            }
            
            showQuestion() {
                if (this.currentQuestion >= this.gameData.questions.length) {
                    this.showFinalResults();
                    return;
                }
                
                const question = this.gameData.questions[this.currentQuestion];
                this.maxScore++;
                
                const content = `
                    <div class="question">
                        <div class="question-text">
                            問${this.currentQuestion + 1}: ${question.text}
                            <span style="float: right; color: #4ecdc4; font-size: 0.8em;">
                                難易度: ${'⭐'.repeat(question.difficulty)}
                            </span>
                        </div>
                        <div class="options">
                            ${question.options.map((option, index) => `
                                <div class="option" onclick="game.selectOption(${index})" data-index="${index}">
                                    ${String.fromCharCode(65 + index)}. ${option}
                                </div>
                            `).join('')}
                        </div>
                        <button class="submit-btn" id="submitBtn" onclick="game.submitAnswer()" disabled>
                            回答を確定する
                        </button>
                        <div class="feedback" id="feedback"></div>
                    </div>
                `;
                
                document.getElementById('gameContent').innerHTML = content;
                this.selectedAnswer = null;
            }
            
            selectOption(index) {
                // 既存の選択を解除
                document.querySelectorAll('.option').forEach(opt => {
                    opt.classList.remove('selected');
                });
                
                // 新しい選択を設定
                document.querySelector(`[data-index="${index}"]`).classList.add('selected');
                this.selectedAnswer = index;
                document.getElementById('submitBtn').disabled = false;
            }
            
            submitAnswer() {
                const question = this.gameData.questions[this.currentQuestion];
                const isCorrect = this.selectedAnswer === question.correct;
                const feedback = document.getElementById('feedback');
                
                // オプションに結果を表示
                document.querySelectorAll('.option').forEach((opt, index) => {
                    opt.style.pointerEvents = 'none';
                    if (index === question.correct) {
                        opt.classList.add('correct');
                    } else if (index === this.selectedAnswer && !isCorrect) {
                        opt.classList.add('incorrect');
                    }
                });
                
                if (isCorrect) {
                    this.score++;
                    feedback.className = 'feedback correct';
                    feedback.innerHTML = `
                        <div class="feedback-title">🎉 正解です！</div>
                        <div class="explanation">${question.explanation}</div>
                        <div class="learning-point">${question.learningPoint}</div>
                        <button class="next-btn" onclick="game.nextQuestion()">次の問題へ</button>
                    `;
                    this.checkAchievements();
                } else {
                    this.wrongAnswers.push({
                        questionNumber: this.currentQuestion + 1,
                        question: question.text,
                        yourAnswer: question.options[this.selectedAnswer],
                        correctAnswer: question.options[question.correct],
                        explanation: question.explanation,
                        learningPoint: question.learningPoint
                    });
                    
                    feedback.className = 'feedback incorrect';
                    feedback.innerHTML = `
                        <div class="feedback-title">💡 学習の機会です</div>
                        <div class="explanation">
                            <strong>正解:</strong> ${String.fromCharCode(65 + question.correct)}. ${question.options[question.correct]}<br><br>
                            <strong>解説:</strong> ${question.explanation}
                        </div>
                        <div class="learning-point">${question.learningPoint}</div>
                        <button class="next-btn" onclick="game.nextQuestion()">次の問題へ</button>
                    `;
                }
                
                feedback.style.display = 'block';
                document.getElementById('submitBtn').style.display = 'none';
                this.updateProgress();
            }
            
            checkAchievements() {
                const scorePercentage = (this.score / this.maxScore) * 100;
                let achievement = null;
                
                if (this.score === 3 && this.currentQuestion === 2) {
                    achievement = { badge: "🌟", title: "完璧なスタート", description: "最初の3問を全て正解しました！" };
                } else if (this.score === 6 && this.currentQuestion === 5) {
                    achievement = { badge: "🎯", title: "コミュニケーション・マスター", description: "コミュニケーション分野で優秀な成績です！" };
                } else if (scorePercentage >= 80) {
                    achievement = { badge: "👑", title: "プロフェッショナル・エキスパート", description: "驚異的な理解力を示しています！" };
                }
                
                if (achievement) {
                    setTimeout(() => {
                        const achievementDiv = document.createElement('div');
                        achievementDiv.className = 'achievement';
                        achievementDiv.innerHTML = `
                            <div class="badge">${achievement.badge}</div>
                            <div><strong>${achievement.title}</strong></div>
                            <div>${achievement.description}</div>
                        `;
                        document.getElementById('gameContent').appendChild(achievementDiv);
                    }, 2000);
                }
            }
            
            nextQuestion() {
                this.currentQuestion++;
                this.updateProgress();
                this.showChapterIntro();
            }
            
            updateProgress() {
                const progress = ((this.currentQuestion) / this.gameData.questions.length) * 100;
                document.getElementById('progressBar').style.width = progress + '%';
                document.getElementById('currentQuestion').textContent = this.currentQuestion + 1;
                document.getElementById('score').textContent = this.score;
                
                // レベル更新
                const scorePercentage = this.maxScore > 0 ? (this.score / this.maxScore) * 100 : 0;
                let level = "見習い";
                if (scorePercentage >= 90) level = "マスター";
                else if (scorePercentage >= 80) level = "エキスパート";
                else if (scorePercentage >= 70) level = "プロ";
                else if (scorePercentage >= 60) level = "上級者";
                else if (scorePercentage >= 40) level = "中級者";
                
                document.getElementById('level').textContent = level;
            }
            
            showFinalResults() {
                const scorePercentage = (this.score / this.maxScore) * 100;
                let finalRank, finalMessage, finalCharacter;
                
                if (scorePercentage >= 90) {
                    finalRank = "グランドマスター・プロフェッショナル";
                    finalMessage = "素晴らしい！あなたは真のプロフェッショナルとしての資質を備えています。";
                    finalCharacter = "👑";
                } else if (scorePercentage >= 80) {
                    finalRank = "エキスパート・プロフェッショナル";
                    finalMessage = "優秀な成績です！プロフェッショナルとしての基盤がしっかりと築かれています。";
                    finalCharacter = "🌟";
                } else if (scorePercentage >= 70) {
                    finalRank = "認定プロフェッショナル";
                    finalMessage = "合格です！基本的な知識は身についています。さらなる向上を目指しましょう。";
                    finalCharacter = "🎯";
                } else if (scorePercentage >= 60) {
                    finalRank = "アシスタント・プロフェッショナル";
                    finalMessage = "もう少しです！基礎を固めて再挑戦しましょう。";
                    finalCharacter = "🌱";
                } else {
                    finalRank = "学習者";
                    finalMessage = "学習の機会として活用し、知識を深めていきましょう。";
                    finalCharacter = "📚";
                }
                
                let weaknessReport = "";
                if (this.wrongAnswers.length > 0) {
                    weaknessReport = `
                        <div class="weakness-report">
                            <div class="weakness-title">📊 復習ポイント</div>
                            ${this.wrongAnswers.map(wrong => `
                                <div class="weakness-item">
                                    <strong>問${wrong.questionNumber}:</strong> ${wrong.question}<br>
                                    <small style="color: #e53e3e;">あなたの回答: ${wrong.yourAnswer}</small><br>
                                    <small style="color: #48bb78;">正解: ${wrong.correctAnswer}</small><br>
                                    <em>${wrong.explanation}</em>
                                </div>
                            `).join('')}
                        </div>
                    `;
                }
                
                const content = `
                    <div class="final-results">
                        <div class="character" style="font-size: 5em;">${finalCharacter}</div>
                        <h2 class="chapter-title">冒険完了！</h2>
                        <div style="font-size: 2em; color: #4ecdc4; margin: 20px 0;">
                            ${this.score} / ${this.maxScore} 点 (${Math.round(scorePercentage)}%)
                        </div>
                        <div style="font-size: 1.5em; font-weight: 600; color: #667eea; margin-bottom: 20px;">
                            ${finalRank}
                        </div>
                        <div style="font-size: 1.2em; margin-bottom: 30px; color: #4a5568;">
                            ${finalMessage}
                        </div>
                        
                        ${weaknessReport}
                        
                        <div style="margin-top: 30px;">
                            <button class="restart-btn" onclick="game.restart()">🔄 もう一度挑戦</button>
                            <button class="restart-btn" onclick="game.restartShuffle()">🎲 ランダムモードで再挑戦</button>
                            <button class="restart-btn" onclick="game.reviewMode()">📖 復習モード</button>
                        </div>
                    </div>
                `;
                
                document.getElementById('gameContent').innerHTML = content;
            }
            
            restart() {
                this.currentQuestion = 0;
                this.score = 0;
                this.maxScore = 0;
                this.wrongAnswers = [];
                this.selectedAnswer = null;
                this.updateProgress();
                this.showChapterIntro();
            }
            
            restartShuffle() {
                // 問題と選択肢をシャッフル
                this.gameData.questions = this.shuffleArray(this.gameData.questions);
                this.gameData.questions.forEach(question => {
                    const correctAnswer = question.options[question.correct];
                    question.options = this.shuffleArray(question.options);
                    question.correct = question.options.indexOf(correctAnswer);
                });
                
                // チャプターの問題インデックスを更新
                this.gameData.chapters.forEach((chapter, chapterIndex) => {
                    const questionsPerChapter = Math.ceil(this.gameData.questions.length / this.gameData.chapters.length);
                    const startIndex = chapterIndex * questionsPerChapter;
                    const endIndex = Math.min(startIndex + questionsPerChapter, this.gameData.questions.length);
                    chapter.questions = [];
                    for (let i = startIndex; i < endIndex; i++) {
                        chapter.questions.push(i);
                    }
                });
                
                this.restart();
            }
            
            shuffleArray(array) {
                const newArray = [...array];
                for (let i = newArray.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [newArray[i], newArray[j]] = [newArray[j], newArray[i]];
                }
                return newArray;
            }
            
            reviewMode() {
                if (this.wrongAnswers.length === 0) {
                    alert("復習する問題がありません！全問正解でした🎉");
                    return;
                }
                
                // 間違えた問題のみを含む新しいゲームデータを作成
                const reviewQuestions = this.wrongAnswers.map(wrong => {
                    return this.gameData.questions.find(q => q.text === wrong.question);
                });
                
                this.gameData.questions = reviewQuestions;
                this.gameData.chapters = [{
                    title: "復習モード",
                    character: "📚",
                    story: "間違えた問題を復習して、知識を確実に身につけましょう。",
                    questions: reviewQuestions.map((_, index) => index)
                }];
                
                this.restart();
            }
        }
        
        // ゲーム開始
        const game = new ConductCodeGame();
    </script>
</body>
</html>
